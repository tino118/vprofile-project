FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt get install maven -y
RUN git clone  https://github.com/devopshydclub/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install 


From tomcat :9-jre11
RUN  rm -rf /usr/local/tomcat/webapps/*
RUN --from=BUILD_IMAGE vprofile-project/target/vprofile-V2.war  /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
 CMD ["catalina.sh", "run"]