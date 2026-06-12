---
title: "set JAVA_HOME"
date: 2011-01-30
forum: General Help
---

### Post by ahso4271 on 2011-01-30
Hi
this is the error:

BUILD FAILED
/home/michael/Android-cpp/android-sdk-linux_x86/tools/ant/main_rules.xml:361: Unable to find a javac compiler;
com.sun.tools.javac.Main is not on the classpath.
Perhaps JAVA_HOME does not point to the JDK.
It is currently set to "/usr/lib/jvm/java-6-openjdk/jre"

so i set it in as described: 
[http://www.cyberciti.biz/faq/linux-unix-set-java_home-path-variable/](http://www.cyberciti.biz/faq/linux-unix-set-java_home-path-variable/)

but it's not working! Ok then i installed jdk from software manager but still the same.
Many thanks
Michael

---

### Post by ahso4271 on 2011-01-30
ok fixed that with:

sudo update-java-alternatives -s java-6-sun

now how should i tell net beans this path? I've two jdk, one in 
/apps/jdk same download/location as /apps/netbeans6-9.1

Thanks

---

