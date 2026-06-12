---
title: "Java Set Path Problem"
date: 2010-03-27
forum: General Help
---

### Post by thanuja on 2010-03-27
Hi All,

I have installed jdk1.6_0_0 to kubuntu 8.10. But javac command doesn't work yet. How do I set path?? Here are the outputs i got from typign some commands
ls -l usr/bin/java ----> etc/alternatives/java
ls -l etc/alternatives/java --->usr/lib/jvm/java-6-openjdk/jre/bin/java

Pls help me on this??

Thanks

---

### Post by spiderbatdad on 2010-03-27
```
$PATH
```
will show you what is in path.

---

### Post by mechro on 2010-03-27
Those outputs are links installed by the java packages to point to the relevant executables. Your paths are probably OK.

What output do you get when you issue the **javac** command?

---

### Post by thanuja on 2010-03-27
This is the output i get when i execute javac command

The program 'javac' can be found in the following packages:
 * gcj-4.2
 * jikes-sun
 * jikes-sablevm
 * kaffe
 * sun-java6-jdk
 * jikes-classpath
 * ecj
 * gcj-4.3
 * cacao-oj6-jdk
 * openjdk-6-jdk
 * jikes-kaffe
 * sun-java5-jdk
 * java-gcj-compat-dev
Try: sudo apt-get install <selected package>
bash: javac: command not found

Wht does this mean??

---

### Post by mechro on 2010-03-27
It means javac isn't installed.

What do you actually want to do with Java? If you just want it to work when you go to a Java web page then you should be good to go.

What were you expecting to happen with the javac command?

---

### Post by krismatth3 on 2010-03-27
Do this

```
# sudo apt-get install sun-java6-jdk
```

Then try again.

---

### Post by thanuja on 2010-03-28
Hi,

Sry When I did that it starts to download. Then it gets stuck in a position which says, package configuration and opens a file 'configuring sun java bin' which i cant close. 

What do i do now?

Pls help..

---

