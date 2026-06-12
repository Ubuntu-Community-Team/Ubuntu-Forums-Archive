---
title: "Java and Classpath- Please Help!"
date: 2009-08-05
forum: General Help
---

### Post by x0dros on 2009-08-05
Hi,
How can I add some jar files to the Java Classpath **permanently **?
my java version is 1.6.0.
Could anyone please help me out with this?
Thnx a lot!

Ps: Sorry if I posted the above under an irrelevant topic! It's my first time in this Forum!

---

### Post by SyL on 2009-08-05
Hi,

read that: [http://ubuntuforums.org/showthread.php?t=217936&highlight=classpath](http://ubuntuforums.org/showthread.php?t=217936&highlight=classpath)

Mainly you define your default JVM using the command 
```
update-java-alternatives
```The classpath is defined per user.
For your own user just add it to your env file:
```
sudo gedit /etc/environment
```
HTH

---

