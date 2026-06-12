---
title: "java working but not plugin"
date: 2012-01-17
forum: General Help
---

### Post by rng on 2012-01-17
In my ubuntu 10.04LTS jre is installed and the commands 'java' and 'javac' are working but firefox is not showing java applets. I have tried following command:

```
ln -s /opt/java/32/jre1.6.0_30/lib/i386/libnpjp2.so ~/.mozilla/plugins/
```But a broken link is created since there is no such source file.

As far as I can see, gcj-jre-headless and gcj-jdk are installed. 

Please help.

---

### Post by grizzler on 2012-01-18
That looks like you have the Java Runtime installed in /opt. Did you put it there manually as mentioned here [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)? Try these terminal commands
```

java -version
update-alternatives --query java
update-alternatives --query jexec
update-alternatives --query mozilla-javaplugin.so

```to see what's installed where exactly.

---

### Post by rng on 2012-01-18
Following are the results: 
```
$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.4.3


$ update-alternatives --query java
Link: java
Status: auto
Best: /usr/bin/gij-4.4
Value: /usr/bin/gij-4.4

Alternative: /usr/bin/gij-4.4
Priority: 1044
Slaves:
 java.1.gz /usr/share/man/man1/gij-4.4.1.gz


$ update-alternatives --query jexec
update-alternatives: error: no alternatives for jexec.


$ update-alternatives --query mozilla-javaplugin.so
update-alternatives: error: no alternatives for mozilla-javaplugin.so.




```

---

### Post by grizzler on 2012-01-19
Apparently you only have an ancient and incomplete Java installation. To be honest, I have no idea how or where you could have gotten hold of 1.5.0. Maybe it came with gcj-jdk?

Anyway, getting applets running in Firefox isn't going to work this way. I suggest you either install OpenJDK or take a look at the webpage I mentioned in my previous message for an alternative.

---

