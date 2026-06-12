---
title: "Tomcat environmental varibles not showing using echo command"
date: 2011-05-30
forum: General Help
---

### Post by mhawila on 2011-05-30
Hi all,
I am running apache-tomcat6 on my laptop and it is working fine. I always start my tomcat server on terminal as follows (i.e. it is not configured to start automatically)
```

willa@willa-laptop:/usr/local/apache-tomcat-6.0.18/bin$ sudo sh startup.sh 
Using CATALINA_BASE:   /usr/local/apache-tomcat-6.0.18
Using CATALINA_HOME:   /usr/local/apache-tomcat-6.0.18
Using CATALINA_TMPDIR: /usr/local/apache-tomcat-6.0.18/temp
Using JRE_HOME:       /usr

```However when I try to see the value of CATALINA_HOME, CATALINA_HOME or CATALINA_TMPDIR either as normal user or superuser (root) I only get a blank line. Below is the command I run to view the contents of these env variables.

```

willa@willa-laptop:/usr/local/apache-tomcat-6.0.18/bin$ echo $CATALINA_HOME

willa@willa-laptop:/usr/local/apache-tomcat-6.0.18/bin$ sudo su -
root@willa-laptop:~# echo $CATALINA_HOME

```1. Why is my system exhibiting this kind of behaviour? 
2  Is there any other way to view contents of these env variables?

Thanks in advance.

---

