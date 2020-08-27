node('master') 
{
    stage('ContinuousDownload') 
    {
       git 'https://github.com/selenium-saikrishna/maven.git'
    }
    stage('ContinuousBuild') 
    {
       sh label: '', script: 'mvn package'
    }
    stage('ContinuousDeployment') 
    {
       sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.14.52:/var/lib/tomcat8/webapps/testenv.war'
    }
    stage('ContinuousTesting') 
    {
        git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
        sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
    }
    stage('ContinuousIntegratioin') 
    {
       sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.0.125:/var/lib/tomcat8/webapps/prodenv.war'
    }
}

