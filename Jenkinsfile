*/** pipeline {
    agent any
     tools {
        maven 'Maven' 
        }
    stages {
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
                slackSend channel: 'youtubejenkins', message: 'Job Started'
                
            }
            
        }
        stage("Build"){
            steps{
                sh "mvn package"
                
            }
            
        }
        stage("Deploy on Test"){
            steps{
                // deploy on container -> plugin
               // deploy adapters: [tomcat9(credentialsId: 'tomcatserverdetails1', path: '', url: 'http://http://3.110.171.140:8080')], contextPath: '/app', war: '**/*.war'
         */**     deploy adapters: [tomcat9(credentialsId: 'awstomcate', path: '', url: 'http://3.110.171.140/')], contextPath: '/app', war: '**/*.war'
            }
            
        */**}
        stage("Deploy on Prod"){
             input {
                message "Should we continue?"
                ok "Yes we Should"
            }
            
            steps{
                // deploy on container -> plugin
              //deploy adapters: [tomcat9(credentialsId: 'tomcatserverdetails1', path: '', url: 'http://3.110.194.43:8080')], contextPath: '/app', war: '**/*.war'
            */**   deploy adapters: [tomcat9(credentialsId: 'awstomcate', path: '', url: 'http://3.110.194.43/')], contextPath: '/app', war: '**/*.war'
            }
       */** }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
             slackSend channel: 'youtubejenkins', message: 'Success'
        }
        failure{
            echo "========pipeline execution failed========"
             slackSend channel: 'youtubejenkins', message: 'Job Failed'
        }
    }
}
*/**
