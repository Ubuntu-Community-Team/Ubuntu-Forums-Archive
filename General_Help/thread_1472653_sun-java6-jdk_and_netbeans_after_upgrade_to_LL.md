---
title: "sun-java6-jdk and netbeans after upgrade to LL"
date: 2010-05-04
forum: General Help
---

### Post by octopus22 on 2010-05-04
Hello ppl!

Have a strange problem. After upgrading my Kubuntu to Lucid Lynx i have issues. Netbeans-php stop working. I was sure it's because i need to reinstall it. 
So i have made 
> sudo apt-get install netbeans
and Netbeans for JAVA only has installed. &#1086;&#1054;

So, i removed it through package manager.

Now i don't have jdk and don't have any working netbeans.

Installer not starts, it tells me i need JDK to install software. I suppose it was removed with netbeans-java. 

BUT, i can't install sun-java6-jdk anymore!

> root@webadmin:/home/xxx/Downloads# sudo sh netbeans-6.8-ml-php-linux.sh 
Configuring the installer...
Searching for JVM on the system...
Java SE Development Kit (JDK) was not found on this computer
JDK 6 or JDK 5 is required for installing the NetBeans IDE. Make sure that the JDK is properly installed and run installer again.
You can specify valid JDK location using --javahome installer argument.

To download the JDK, visit [http://java.sun.com/javase/downloads](http://java.sun.com/javase/downloads)


root@webadmin:/home/xxx/Downloads# sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jdk has no installation candidate
root@webadmin:/home/sunsay/Downloads# 


Yes, i'm on amd64, but i have seen Netbeans with Java worked OK.
What can i do now to go back to work?

---

### Post by philinux on 2010-05-04
Have a look at the forum stick re lucid.

---

### Post by octopus22 on 2010-05-04
Ok, i understand no more support for sun-java6-jdk, but how it worked with netbeans on lucid? Can i install it manually?
Apt-get have no package like open-jdk or openjdk...

And the most important - what to do with all this stuff?  i need netbeans to work

---

### Post by Morbius1 on 2010-05-04
Take a look at this: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

It talks about the Sun JRE not the JDK but once you enable the repository you'll have access to both.

---

### Post by octopus22 on 2010-05-04
was tricky a bit.

i have installed open-jre with aptitude, not apt-get.. (what's the diff, btw?)
Netbeans still not worked. So i found it's directory, run uninstall.sh. Then installed Netbeans from scratch. 
All working now again, thanks for help!

---

