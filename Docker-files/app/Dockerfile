FROM openjdk:11 AS BUILD_IMAGE
RUN apt-get update && apt-get install -y maven
RUN git clone https://github.com/omaraliii1/vprofile-project.git
RUN cd vprofile-project &&git checkout docker  && mvn install

FROM tomcat:9-jdk11-openjdk 
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/*.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
