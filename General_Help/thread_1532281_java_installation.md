---
title: "java installation"
date: 2010-07-16
forum: General Help
---

### Post by puzhakkara on 2010-07-16
i have installed java.but not available in firefox.the web pages which needs java are still not loading

the following is my java config

root@puzhakkara-laptop:~# java -version
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8) (6b18-1.8-0ubuntu1)
OpenJDK Client VM (build 14.0-b16, mixed mode, sharing)
root@puzhakkara-laptop:~# 


how to make java work on firefox or opera

help needed


greetings

---

### Post by kerry_s on 2010-07-16
install "ubuntu-restricted-extras" & get all that stuff taken care of.

---

### Post by ajgreeny on 2010-07-16
Some, not many, web sites will not work with openJDK, only with sun-java, so you may need to replace the openjdk with sun's version, in the partner repos.

---

### Post by puzhakkara on 2010-07-16
hi ok thanks for the reply.pls read the below also

actually i have installed the java(self extracting) from java.com and it is existing in /usr/java

also created a symbolic link to the firefox 3.6.6 plugin folder according to the instructions from the java.com page

there are two or three firefox folders in /usr/lib

which is the correct one to make symbolic link

the funny thing is that my firefox 3.6.6 plugins shows java plugin very clearly

but unfortunately firefox not loads the web pages (which need java) like in windows

thanks for the help

---

### Post by QIII on 2010-07-16
You installed Sun Java Update 20?


For future reference:  

**If you are using Lucid**

It would have been best if you had not installed directly from the Java website.  Every time a new update comes out, you will have to follow that procedure again.

If I were you, I would follow the instructions to uninstall Java.  Then, go to System | Administration | Software Sources.  On the "Other Software" tab, check the partner repo and allow your sources to refresh.

Then use Synaptic to install the java6-sun packages.

That way, when the packages are updated by Oracle and put into the repository, Java will be automatically updated without having to go back to the Java website.

---

