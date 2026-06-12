---
title: "need explanation regarding libreoffice"
date: 2012-04-29
forum: General Help
---

### Post by bostjanv on 2012-04-29
Hello,
I just started using Ubuntu 12.04, and I encountered the following: when I start libreoffice by clicking on the taskbar (or whatever) everything works as expected; however, when I start libreoffice from the command line by typing "libreoffice", I get the following message:

bostjan@ubuntu:~$ libreoffice
javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package libreoffice-java-common
is installed.
If it is already installed then try removing ~/.libreoffice/3/user/config/javasettings_Linux_*.xml
Warning: failed to read path from javaldx


EVEN THOUGH libreoffice (apparently) runs OK. Should I do anything?

Regards,
bostjanv

---

### Post by Steven D on 2012-05-03
Actually I had this problem on my windows machine as well. Reinstalling java, then running the main LibreOfiice suite solved on windows.
on my Ubuntu machine using OpenJDK i didn't receive this error. I did install java before running libreoffice, not sure if that has anything to do with it.
try clicking on Tools -- Options -- LibreOffice -- Java and see if it says anything there.

---

### Post by kc1di on 2012-05-03
if you haven't already install Openjdk6 java runtime seems to work here with Libreoffice. It's in the repository.

---

### Post by jarathomas on 2012-06-06
I was receiving that message and found this

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/926594](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/926594)

which suggests running

sudo apt-get install libreoffice-base

This worked for me.

---

