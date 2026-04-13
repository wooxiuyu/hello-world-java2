pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/wooxiuyu/hello-world-java2.git'
            }
        }
        stage('Build') {
            steps { bat 'gradlew clean build'}
        }
        stage('Test') {
            steps { bat 'gradlew test'}
        }
        stage('Deploy') {
            steps { powershell 'java -cp build/libs/hello-world-java2.jar com.example.HelloWorld' }           
        }    
}

post {
        always {
            echo 'Cleaning up workspace'
            deleteDir() // Clean up the workspace after the build
        }
        success {
            echo 'Build succeeded!!!'
            // You could add notification steps here
        }
        failure {
            echo 'Build failed!'
            // You could add notification steps here
        }
    }
    
}
