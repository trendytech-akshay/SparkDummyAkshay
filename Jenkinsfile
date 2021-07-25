pipeline {
    agent any
    tools {
        maven 'maven363'
    }
    environment {
        ITVERSITY = credentials('itversity')
    }
    stages {
        stage('Compile') { 
            steps {
                sh 'cd SparkWordCount && mvn clean compile' 
            }
        }
        stage('Unit Test') { 
            steps {
                sh 'cd SparkWordCount && mvn clean test'
            }
        }
        stage('Package') { 
            steps {
                sh 'cd SparkWordCount && mvn clean package'
            }
        }    
        stage('Deploy') {
            steps{
                sh 'gsutil cp SparkWordCount/target/SparkWordCount-1.0-SNAPSHOT.jar gs://codejar/'
            }
        }
    }
}

