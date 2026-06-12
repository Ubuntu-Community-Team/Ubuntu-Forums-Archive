---
title: "tomcat7, default install does not listen?"
date: 2012-03-30
forum: General Help
---

### Post by metalfan_ on 2012-03-30
hi,

ive purged tomcat7 and removed some left over files from /etc/tomcat/
(btw, shouldnt purge kill all files from the package?)

after reinstalling and starting tomcat via the init scripts it does not listen on any ports?

```

netstat -pln --inet 

```
doesnt show tomcat

what might be the problem?

catalina.2012-03-30.log
```

Mar 30, 2012 6:39:38 PM org.apache.coyote.AbstractProtocol init
INFO: Initializing ProtocolHandler ["http-bio-8080"]
Mar 30, 2012 6:39:38 PM org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 1111 ms
Mar 30, 2012 6:39:38 PM org.apache.catalina.core.StandardService startInternal
INFO: Starting service Catalina
Mar 30, 2012 6:39:38 PM org.apache.catalina.core.StandardEngine startInternal
INFO: Starting Servlet Engine: Apache Tomcat/7.0.23
Mar 30, 2012 6:39:38 PM org.apache.catalina.startup.HostConfig deployDirectory
INFO: Deploying web application directory /var/lib/tomcat7/webapps/ROOT
Mar 30, 2012 6:39:40 PM org.apache.coyote.AbstractProtocol start
INFO: Starting ProtocolHandler ["http-bio-8080"]
Mar 30, 2012 6:39:40 PM org.apache.catalina.startup.Catalina start
INFO: Server startup in 1581 ms

```

the other log files are empty, catalina.out is a copy of the above.

---

### Post by metalfan_ on 2012-03-30
looks like tomcat is indeed listening

```

wget http://myip:8080

```

returns a permission denied

but why is it not listed by netstat?

---

### Post by dragonfly41 on 2012-03-30
This netstat command works .. for me .. I have tomcat7 running

[http://geekbrigade.wordpress.com/2009/02/26/how-to-find-and-kill-a-process-that-is-using-a-particular-port-in-ubuntu/](http://geekbrigade.wordpress.com/2009/02/26/how-to-find-and-kill-a-process-that-is-using-a-particular-port-in-ubuntu/)

sudo netstat -lpn | grep :8080

---

### Post by metalfan_ on 2012-04-03
ah yes, --inet does only show ipv4.

thx

---

