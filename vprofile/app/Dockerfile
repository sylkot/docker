FROM openjdk:8 AS BUILD_IMG
RUN apt update && apt install maven -y
RUN git clone -b vp-rem https://github.com/devopshydclub/vprofile-project.git 
RUN cd vprofile-project && mvn install

FROM tomcat:8-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMG vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
WORKDIR /usr/local/tomcat/
VOLUME /usr/local/tomcat/webapps