---
title: "TOMCAT ON LINUX - HTTP Status 404 - /webapps"
date: 2011-06-18
forum: General Help
---

### Post by imrairai on 2011-06-18
Hi,

I've been having this problem for quite a long time now. I can't access the webapps folder ([http://localhost:8080/webapps](http://localhost:8080/webapps)) in the tomcat6 directory to run files. But whenever I try to access [http://localhost:8080/docs](http://localhost:8080/docs) and [http://localhost:8080/examples](http://localhost:8080/examples) it's accessible. 

It says this one:

**HTTP Status 404 - /webapps**

**type** Status report
**message** _/webapps_
**description** _The requested resource (/webapps) is not available._
**Apache Tomcat/6.0.24**


I don't know what's happening but since I installed it I cannot run files like jsp and war files. 

Is there any configuration needed whatsoever?

Btw, whenver I try to access [http://localhost:8080/](http://localhost:8080/) this is what I get:

**It works !**

  If you're seeing this page via a web browser, it means you've setup Tomcat successfully. Congratulations!
   This is the default Tomcat home page. It can be found on the local filesystem at: /var/lib/tomcat6/webapps/ROOT/index.html
  Tomcat6 veterans might be pleased to learn that this system instance of Tomcat is installed with CATALINA_HOME in /usr/share/tomcat6 and CATALINA_BASE in /var/lib/tomcat6, following the rules from /usr/share/doc/tomcat6-common/RUNNING.txt.gz.
  You might consider installing the following packages, if you haven't already done so:
  **tomcat6-docs**: This package installs a web application that  allows to browse the Tomcat 6 documentation locally. Once installed, you  can access it by clicking [here]("http://localhost:8080/docs/").
  **tomcat6-examples**: This package installs a web application that  allows to access the Tomcat 6 Servlet and JSP examples. Once installed,  you can access it by clicking [here]("http://localhost:8080/examples/").
  **tomcat6-admin**: This package installs two web applications that can help managing this Tomcat instance. Once installed, you can access the [manager webapp]("http://localhost:8080/manager/html") and the [host-manager webapp]("http://localhost:8080/host-manager/html").
  
NOTE: For security reasons, using the manager webapp is  restricted to users with role "manager". The host-manager webapp is  restricted to users with role "admin". Users are defined in /etc/tomcat6/tomcat-users.xml.


Is this normal? Please help! Advance thank you!!!!

---

### Post by pramod.niralakeri on 2011-10-22
even i've same problem...have u got any solution?

---

### Post by zowo on 2011-11-02
i've got the same problem, i installed tinyPM and got the error-message

```
HTTP Status 404 - /login.jsf

type Status report

message /login.jsf

description The requested resource (/login.jsf) is not available.

Apache Tomcat/6.0.28
```

does anybody can give me a hint?

---

### Post by alexy4chat on 2011-12-31
> **zowo said:**
> i've got the same problem, i installed tinyPM and got the error-message

```
HTTP Status 404 - /login.jsf

type Status report

message /login.jsf

description The requested resource (/login.jsf) is not available.

Apache Tomcat/6.0.28
```

does anybody can give me a hint?
Sun Secure Global Desktop amin console cannot open, error below

HTTP Status 404 -/sgdadmin/
type Status report
message /sgdadmin/
description The requested resource (/sgdadmin/) is not available

Apache Tomcat/6.0.32

---

