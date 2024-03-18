FROM openjdk:11 as BUILD_IMAGE
RUN apt update && apt install -y maven
RUN git clone https://github.com/sidhu2003/vprofile-app.git
RUN cd vprofile-app && mvn install

FROM tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE /vprofile-app/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]

