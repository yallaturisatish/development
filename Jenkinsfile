pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/yallaturisatish/dev.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
                sh 'scp /home/ubuntu/jenkins/workspace/webapp/target/webapp.war ubuntu@172.31.47.214:/var/lib/tomcat8/webapps/newtestapp.war'
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/yallaturisatish/Testing.git'
                sh 'java -jar /home/ubuntu/jenkins/workspace/DeclarativePipeline/testing.jar'
            }
        }
        stage('ContinuousDelivery')
        {
            steps
            {
                 sh 'scp /home/ubuntu/jenkins/workspace/webapp/target/webapp.war ubuntu@172.31.47.86:/var/lib/tomcat8/webapps/newprodapp.war'
            }
        }
    }
}
