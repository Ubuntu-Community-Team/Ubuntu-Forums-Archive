---
title: "Need to set defualt java"
date: 2009-12-19
forum: General Help
---

### Post by tech newbie on 2009-12-19
<-------------Read my username First!




I installed latest version of java via the following .bin file, jre-6u17-linux-i586.bin
I creates a folder called,    jre1.6.0_17
The directory of this folder is  /home/home/jre1.6.0_17  (my username i log in with is called home)
 I followed these instructions to set default java
> **Choosing the default Java to use**

 Just installing new Java flavours does not change the default Java pointed to by /usr/bin/java.  You must explicitly set this: 

[LIST]
[*]Open a Terminal window
[*]Run sudo update-java-alternatives -l to see the current configuration and possibilities.
[*]Run sudo update-java-alternatives -s XXXX to set the XXX java version as default.  For Sun Java 6 this would be sudo update-java-alternatives -s java-6-sun
[*]Run java -version to ensure that the correct version is being called.
[/LIST]
The only option is for open-jdk, not sun java. I need to set it as defualt.

---

### Post by tech newbie on 2009-12-19
When it is set as default I will also need it configured for FireFox.

---

### Post by tech newbie on 2009-12-19
Bump?

---

### Post by tech newbie on 2009-12-19
bump

---

### Post by tech newbie on 2009-12-19
still no reply

---

### Post by tech newbie on 2009-12-19
I managed to sign in as root and install java here, /usr/lib/jvm/jre1.6.0_17

Stil wont let me set as defualt

---

