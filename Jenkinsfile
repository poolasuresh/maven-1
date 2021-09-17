mpipeline {
    agent any
tools {
    maven 'maven'
}
    stages {
        stage('gitcheckout') {
            steps {
                 checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/poolasuresh/maven-1.git']]])
            }
        }
        stage('build') {
         steps {
             bat 'mvn clean install'
            
        }
        }
        stage('deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: '2067cda4-19a5-473c-9ec2-1a1a79ab9fe3', path: '', url: 'http://localhost:8070/')], contextPath: 'maven-1', war: '**/*.war'
               
                           }
        }
    }
}

