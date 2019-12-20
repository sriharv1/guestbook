pipeline {
    environment {
        def repo="hv024036"
        // def date = new Date().format( 'yyyyMMdd' )
        def image="guestbookphp:latest"
        def artifacturl="hub.docker.com"
        def fullPath="https://hub.docker.com//${repo}/${image}"
        // def hostname = "C3PODEV01.NORTHAMERICA.CERNER.NET"
        def name = "guestbookphp"
    }
    agent any 
    stages{
        stage('BUILD'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'docker', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    // sh "docker login ${artifacturl} --username $USERNAME --password $PASSWORD"
                    sh "ls -ltr"
                    sh "docker image build -t ${image} ."
                    sh "docker tag ${image} ${fullPath}"
                    sh "docker push ${fullPath}"
                }
            }
        }
    }  
}
