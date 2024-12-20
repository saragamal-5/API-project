pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // بناء المشاريع باستخدام .NET CLI
                sh 'dotnet build SOAPService.sln'
                sh 'dotnet build RESTApi.sln'
                sh 'dotnet build GrpcService.sln'
            }
        }
        stage('Test') {
            steps {
                // اختبار المشاريع
                sh 'dotnet test'
            }
        }
        stage('Docker Build') {
            steps {
                // بناء صورة Docker للمشاريع
                sh 'docker-compose build'
            }
        }
        stage('Deploy') {
            steps {
                // نشر المشاريع باستخدام Docker
                sh 'docker-compose up -d'
            }
        }
    }
}
