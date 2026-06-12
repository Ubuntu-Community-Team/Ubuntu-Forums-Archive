---
title: "Java error - &quot;could not find Java 2 Runtime Environment&quot;"
date: 2009-09-22
forum: General Help
---

### Post by adun153 on 2009-09-22
I've been trying to run a jar file with "java -jar <jarfile path>, and it keeps giving me this error:

Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.


Note: libjava.so exists and is located at the following:

/usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
/usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/i386/libjava.so

I've even tried copying libjava.so to /lib and still nothing.

I've tried reinstalling the java6-sdk and jre packages and it still didn't work. Any ideas? Thanks!

---

### Post by bogdan.veringioiu on 2009-09-23
Hi.

What is your default java executable?
Try to type this in terminal:
$which java

What is the output?
Bogdan

---

### Post by adun153 on 2009-09-25
$ which java
/usr/bin/java

"ls -l /usr/bin/java" tells me that it isn't a link.

Thanks!

---

### Post by bogdan.veringioiu on 2009-09-25
Hi.
It looks to me that the default java executable in your system is not sun's jdk.
What is the output of java --version?
How did you install sun jdk/jre? Via ubuntu repos?

Bogdan

---

### Post by credobyte on 2009-09-25
```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by adun153 on 2009-09-25
$ java --version
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.

Yes, i got my java from the Ubuntu repos by doing:
sudo apt-get install sun-java6-jdk  sun-java6-jre


tries this:

sudo update-java-alternatives -s java-6-sun no difference. thanks, though.

---

