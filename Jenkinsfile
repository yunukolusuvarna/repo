pipeline {
    agent any
    stages {
        stage('clone-repo') {
            steps {
                // Correct checkout step
                git url: 'https://github.com/yunukolusuvarna/repo.git', branch: 'main'
            }
        }
        stage('build') {
            steps {
                sh 'mvn install'
            }
        }
        stage('compile') {
            steps {
                sh 'mvn package'
            }
        }
        stage('tests') {
            steps {
                sh 'mvn test'
            }
        }
        stage('package as war') {
            steps {
                sh 'mvn package'
            }
        }
        stage('deployment') {
            steps {
                sh 'sshpass -p vpath scp target/gamutkart.war vpath@13.55.138.141:/home/vpath/apache-tomcat-8.5.100/webapps'
            }
        }
    }
}
