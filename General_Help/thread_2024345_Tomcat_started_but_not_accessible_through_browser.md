---
title: "Tomcat started but not accessible through browser"
date: 2012-07-13
forum: General Help
---

### Post by Karita on 2012-07-13
Apologies if this is the wrong forum - I couldn't find an obvious one for Tomcat issues.

I have Tomcat installed and started successfully. As in the log says it's started... 

INFO: Deploying configuration descriptor examples.xml
Jul 13, 2012 10:14:27 PM org.apache.catalina.startup.HostConfig deployDescriptor
INFO: Deploying configuration descriptor manager.xml
Jul 13, 2012 10:14:27 PM org.apache.coyote.http11.Http11Protocol start
INFO: Starting Coyote HTTP/1.1 on http-8080
Jul 13, 2012 10:14:27 PM org.apache.catalina.startup.Catalina start
INFO: Server startup in 380 ms


and 8080 is showing as being used by a java process...

tcp6       0      0 127.0.0.1:8005          :::*                    LISTEN      4805/java
tcp6       0      0 :::8080                 :::*                    LISTEN      4805/java
udp6       0      0 fe80::f03c:91ff:fea:123 :::*                                2624/ntpd

I'm not getting a response back from the browser. It just times out. The odd thing is the IP address before the port - there isn't one!

I've installed Tomcat using apt-get install etc and not knowingly changed anything that would affect the IP address.

The only thing I changed was to set CATALINA_BASE = /var/lib/tomcat6 as out of the box it gets set to CATALINA_HOME by default and this doesn't have log or conf dirs. 

I'm surprised it doesn't work out of the box but I'm new to Ubuntu so could be doing something silly.

Any help appreciated.

---

### Post by Rexilion on 2012-07-14
Do you have IPV6 only connectivity??

---

