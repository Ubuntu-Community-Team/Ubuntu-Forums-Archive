---
title: "Apache Tomcat virtual host configuration"
date: 2010-06-09
forum: General Help
---

### Post by Thyagaraj on 2010-06-09
I've apachectl installed(downloading & extracting "httpd-2.0.62.tar.gz" to /usr/local/apache) having the default apache(/etc/apache2) and Tomcat is installed(/usr/share/tomcat) & is configured for port forwarding(to port 80). i.e without typing [http://ip:8080/](http://ip:8080/) i can directly access by typing [http://ip/](http://ip/) or along with any virtual host under tomcat/webapps.

I've lot of applications under tomcat/webapps which are created using java css xml php scripting languages.

What i want is virtual host configuration,
I want to configure a virtual host under "/usr/local/apache/conf/httpd.conf" with the DocumentRoot of "/usr/share/tomcat/webapps"

for e.g: if i type [http://ip/](http://ip/) i should directly get an application which is located under tomcat/webapps (or) else if it could be done editing the "/usr/share/tomcat/conf/server.xml " file then it's fine.

plz... anyone help to sort out this problem

---

### Post by Thyagaraj on 2010-06-16
Please anyone do reply to this.........

---

