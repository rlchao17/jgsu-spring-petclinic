pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }

    stages {
        // stage('Checkout') {
        //     steps {
        //         git url: 'https://github.com/rlchao17/jgsu-spring-petclinic.git', branch: 'main'
        //     }
        // }
        
        // implicit checkou stage

        stage('Build') {
            steps {
                sh './mvnw clean package'
                // sh 'true'
            }

            post {
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
                // changed {
                //     emailext attachLog: true, 
                //     body: '"Please go to ${BUILD_URL} and verify the build"', 
                //     compressLog: true, 
                //     recipientProviders: [upstreamDevelopers(), requestor()], 
                //     subject: '"Job \'${JOB_NAME}\' (${BUILD_NUMBER}) is waiting for input"', 
                //     to: 'richard.shao@ingka.ikea.com'
                // }
            }
        }
    }
}
