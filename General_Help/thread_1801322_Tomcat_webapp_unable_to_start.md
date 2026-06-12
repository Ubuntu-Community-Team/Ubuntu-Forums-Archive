---
title: "Tomcat webapp unable to start"
date: 2011-07-10
forum: General Help
---

### Post by deaner75 on 2011-07-10
I am running Server 11.04 / Tomcat 7.0.16 / Sysaid ( webapp ) 
 
I have configured the Java environment, tomcat is up and running and moved the sysaid.war to the webapps folder in tomcat.
 
I got to [http://127.0.0.1:8080](http://127.0.0.1:8080) - verify that sysaid is listed as an app, it is. The .war has extracted in the webapps folder but fails to start.
 
Everytime I try to start it I get:
 
"FAIL - Application at context path /sysaid can not be started".. 
 
Anyone have thoughts regarding the fail to run the app? I have hit up sysaid forums, but no luck through searching and or replys at this time...
 
thanks:D

---

### Post by Azdour on 2011-07-11
Hi,

Are there any errors in the catalina.out log that may indicate that the webapp could not be initialised when Tomcat started or the webapp was dropped into Tomcat?

---

