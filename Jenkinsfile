pipeline {
    agent {
        label "jenkins-worker1"
    }

    stages {
        stage('Dotnet Verification') {
            steps {
                sh "dotnet --version"
            }
        }
        
        stage('Compile Application') {
            steps {
                sh "rm -rf /home/jenkins/pipeline-romell/bin/"
                sh "dotnet publish --self-contained -r linux-x64 -c Release"
            }
        }
        
        stage('Deploy Application') {
            steps {
                sh "rm -rf /tmp/proyecto-compilado/*"
                sh "cp -rf /home/jenkins/pipeline-romell/bin/Release/net5.0/linux-x64/publish/* /tmp/proyecto-compilado"
            }
        }
    }
}
