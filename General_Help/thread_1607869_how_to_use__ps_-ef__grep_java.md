---
title: "how to use  ps -ef | grep java"
date: 2010-10-28
forum: General Help
---

### Post by miko5054 on 2010-10-28
i using g tomcat and sometimes it binds and cant run so i have to restart the machine.. i now that i can use 
```
ps -ef | grep java 
``` 
than id receive that 
```
  mik       9923     1  0 15:25 ?        00:00:11 /usr/lib/jvm/java-6-openjdk/bin/java -Dcatalina.base=/home/mik/workspace/.metadata/.plugins/org.eclipse.wst.server.core/tmp0 -Dcatalina.home=/home/mik/workspace\test/apache-tomcat-5.5.31 -Dwtp.deploy=/home/mik/workspace/.metadata/.plugins/org.eclipse.wst.server.core/tmp0/wtpwebapps -Djava.endorsed.dirs=/home/mik/workspace\test/apache-tomcat-5.5.31/common/endorsed -Dfile.encoding=UTF-8 -classpath /home/mik/workspace\test/apache-tomcat-5.5.31/bin/bootstrap.jar:/usr/lib/jvm/java-6-openjdk/lib/tools.jar org.apache.catalina.startup.Bootstrap start
mik      10793 10691  0 15:59 pts/0    00:00:00 grep --color=auto java

```

what next??

thanks
miki

---

### Post by coffee412 on 2010-10-28
> **miko5054 said:**
> i using g tomcat and sometimes it binds and cant run so i have to restart the machine.. i now that i can use 
```
ps -ef | grep java 
```than id receive that 
```
  mik       9923     1  0 15:25 ?        00:00:11 /usr/lib/jvm/java-6-openjdk/bin/java -Dcatalina.base=/home/mik/workspace/.metadata/.plugins/org.eclipse.wst.server.core/tmp0 -Dcatalina.home=/home/mik/workspace\test/apache-tomcat-5.5.31 -Dwtp.deploy=/home/mik/workspace/.metadata/.plugins/org.eclipse.wst.server.core/tmp0/wtpwebapps -Djava.endorsed.dirs=/home/mik/workspace\test/apache-tomcat-5.5.31/common/endorsed -Dfile.encoding=UTF-8 -classpath /home/mik/workspace\test/apache-tomcat-5.5.31/bin/bootstrap.jar:/usr/lib/jvm/java-6-openjdk/lib/tools.jar org.apache.catalina.startup.Bootstrap start
mik      10793 10691  0 15:59 pts/0    00:00:00 grep --color=auto java

```what next??

thanks
miki

If you want to kill a process then just issue :

sudo killall -9 <process name>

That should do it. But you still have to figure out why java crashes which is/has been a common problem.

---

### Post by miko5054 on 2010-10-28
i cant figure out the process name....

---

### Post by SlugSlug on 2010-10-28
from the above example use


sudo kill 9923

---

### Post by anarchy404 on 2010-10-28
If you can help it, try not to use "killall -9". The -9 argument does not allow the process to write off any temporary files, unlock locked files, etc.

grep searches through input files, so perhaps you need to make a temporary file or assign the input to a variable and have grep read from that? I'm not entirely sure. My bash skills are pretty weak at the moment. I hope that helped.

---

