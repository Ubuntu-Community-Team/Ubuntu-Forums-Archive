---
title: "Eclipse + tomcat can't start correctly"
date: 2011-02-02
forum: General Help
---

### Post by kossell on 2011-02-02
Hi, I promise I did search before and I managed to solve many problem but not this one :S

I got jdk, jre, tomcat, eclipse installed correctly (I'm sure about that)

I can start tomcat and works fine, and eclipse too.
but whenever I try to run server through eclipse (server->run) I got following message:

```
WARNING: Failed to create work directory [/home/kossel/workspace/.metadata/.plugins/org.eclipse.wst.server.core/tmp0/work/Catalina/localhost/_] for context []
Feb 2, 2011 6:08:23 PM org.apache.jasper.EmbeddedServletOptions <init>
SEVERE: The scratchDir you specified: /home/kossel/workspace/.metadata/.plugins/org.eclipse.wst.server.core/tmp0/work/Catalina/localhost/_ is unusable.
Feb 2, 2011 6:08:23 PM org.apache.catalina.startup.HostConfig start
SEVERE: Unable to create directory for deployment: /home/kossel/workspace/.metadata/.plugins/org.eclipse.wst.server.core/tmp0/conf/Catalina/localhost

```

tomcat seems launched fine, but it keep saying 404 resource not found including the manager (if I launch tomcat via command, works fine).

did ls -ln workspace I get:
```
drwxr-xr-x 4 1000 1000 4096 2011-02-02 16:34 Servers
```
looks has permission right?
any idea?

---

### Post by kossell on 2011-02-02
For who may interest, 
I did "ls -l" and discovered those folders' owner are root... I don't know how in a user home folders there are root's folder. so I just did chown to the right owner and done!

---

