---
title: "Ubuntu - Adempiere - RUN_Server2.sh"
date: 2010-11-27
forum: General Help
---

### Post by vortuna on 2010-11-27
I reinstall my ubuntu 10.04 server yesterday. Before this server run Adempiere 360 Application

The Setup complite, but when I run the application this error come out.

20:07:33,865 ERROR [STDERR] log4j:ERROR A "org.jboss.logging.appender.FileAppender" object is not assignable to a "org.apache.log4j.Appender" variable.
20:07:33,866 ERROR [STDERR] log4j:ERROR The class "org.apache.log4j.Appender" was loaded by 
20:07:33,866 ERROR [STDERR] log4j:ERROR [WebappClassLoader
delegate: false
repositories:
/WEB-INF/classes/
----------> Parent Classloader:
java.net.FactoryURLClassLoader@153d79c
] whereas object of type 
20:07:33,866 ERROR [STDERR] log4j:ERROR "org.jboss.logging.appender.FileAppender" was loaded by [org.jboss.system.server.NoAnnotationURLClassLoader@fd13b5].
20:07:33,866 ERROR [STDERR] log4j:ERROR Could not instantiate appender named "FILE".

Need help what happen and how to pass this error.

Thank you and regards.

---

### Post by vortuna on 2010-11-27
Help any one pls

---

### Post by giuliano1969 on 2011-03-05
Could be helpful if you specify which installation instruction followed the first time, and which ones the second time.

Any information ?


Often similar problem happen when different operations/installation have been performed.

I deeply suggest to test the install in a Virtual machine, then to write an script to reproduce the install automatically, so that recreating the whole sistem is just a matter of runnin a .sh.

---

