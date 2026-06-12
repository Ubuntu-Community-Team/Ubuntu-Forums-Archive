---
title: "Run 32bit Program on 64bit System Fails"
date: 2010-04-12
forum: General Help
---

### Post by uRock on 2010-04-12
Hello,

I am trying to install Cisco Packet Tracer on my system and it just doesn't wanna go. It is a 32bit .bin installer file. I have tries adding -f(force) to the install command and it still says no.

Are there any ideas that may help me get this installed other than VBox or dual booting?

Here is the output of the attempted install. 

```
rabbit@rabbit-desktop:~$ chmod +x Pack*
rabbit@rabbit-desktop:~$ sudo ./Pack* -f
Self extracting archive...

Welcome to Cisco Packet Tracer 5.2.1 Installation
Read the following End User License Agreement "EULA" carefully. You must accept the terms of this EULA to install and use Cisco Packet Tracer 5.2.1.
Press the Enter key to read the EULA.

Cisco Networking Academy Packet Tracer (5.2) Software License Agreement

<<<EULA statement removed>>>
Do you accept the terms of this EULA? (Y)es/(N)o
y
You have accepted the terms to the EULA. Congratulations. Packet Tracer will now be installed.
Attempting to install package now
dpkg: error processing PacketTracer-5.2-u.i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 PacketTracer-5.2-u.i386.deb
rabbit@rabbit-desktop:~$
```

---

### Post by jobix on 2010-04-13
Check this thread. It might have something:

[http://ubuntuforums.org/showthread.php?p=8138633](http://ubuntuforums.org/showthread.php?p=8138633)

---

