node{
properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
def mavenHome = tool name: 'maven3.9.1'
echo "the job name is: ${JOB_NAME}"
echo "the node name is: ${NODE_NAME}"
echo "the build number is: ${BUILD_NUMBER}"
echo "Jenkins home path is: ${JENKINS_HOME}"

stage('CheckoutCode')
{
git branch: 'development', credentialsId: 'aa7436b2-46cc-4d9b-885d-009780844447', url: 'https://github.com/srinath549-devops/maven-web-application.git'
}

stage('Build')
{
sh "${mavenHome}/bin/mvn clean package"
}
 /*
stage('SonarQubeReport')
{
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('UploadartifactintoNexus')
{
sh "${mavenHome}/bin/mvn clean deploy"
}

stage('DeployintoTomcat')
{
sshagent(['40fef01a-b93a-49ac-9bed-abf44fe696a7']) 
{
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.44.121:/opt/apache-tomcat-9.0.73/webapps"    
}
}
*/
}//nodeclosing
