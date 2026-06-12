---
title: "need help with Tomcat"
date: 2010-10-19
forum: General Help
---

### Post by lapedro on 2010-10-19
Hi
I have a problem with Tomcat.
I have one program, called OLAT, and it need Tomcat to run.
When I start OLAT, tomcat is should be runned automatically with it. But if I start OLAT, the terminal write me back this:

peter@peter-laptop:~/OLAT$ sudo ./runOlat.sh
[sudo] password for peter: 
Using CATALINA_BASE:   ./tomcat-6.0.26
Using CATALINA_HOME:   ./tomcat-6.0.26
Using CATALINA_TMPDIR: /home/peter/OLAT
Using JRE_HOME:        /usr
Using CLASSPATH:       ./tomcat-6.0.26/bin/bootstrap.jar

******************************************************************************************
Tomcat is starting and will deploy OLAT. Be patient, this takes quite a while the first time...
The script will try to connect and inform you when you can lauch: [http://localhost:8080/olat/](http://localhost:8080/olat/)
You can always start this tomcat by running: ./tomcat-6.0.26/bin/startup.sh
******************************************************************************************

--2010-10-20 00:41:34--  [http://localhost:8080/olat/dmz/](http://localhost:8080/olat/dmz/)
Resolving localhost... ::1, 127.0.0.1
Connecting to localhost|::1|:8080... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-10-20 00:41:34 ERROR 404: Not Found.


******************************************************************************************
Tomcat is now up an running. Go to: [http://localhost:8080/olat/](http://localhost:8080/olat/) and enjoy OLAT!
******************************************************************************************

run stopOlat.sh to stop tomcat. This is the same as ./tomcat-6.0.26/bin/shutdown.sh


whats the problem..???

---

