pipeline {
    agent any

    tools {
        maven 'Maven 3.8.6'  // Set this according to your Jenkins Maven config
        jdk 'JDK 11'         // Set this according to your Jenkins JDK config
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/yourusername/V2.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Archive Results') {
            steps {
                junit 'target/surefire-reports/*.xml'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed.'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
