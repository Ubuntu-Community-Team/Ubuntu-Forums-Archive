---
title: "NetBeans 7.0 installation problem"
date: 2011-05-29
forum: General Help
---

### Post by t0m3kk on 2011-05-29
Hi everyone!

Since 20 minutes I tried to install **netbeans-7.0-ml-php-linux.sh** but it won't install and I can't understand where is the problem...

I thought the problem was in JKD because the version I used was 6u24 and I was updated it to 6u25 but I have the same problem... I tried it again when I'm a root user and it was the same situation...

I attaching a image with the method I used and I think the problem is this "**null**" at 8 line but I'm not sure... 

With regards,
George!

---

### Post by linuxinstalledfromhdd on 2011-05-29
Do you really want to install it that way?

Do a search on the following page for Netbeans to install it from the command line:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by t0m3kk on 2011-05-29
> **linuxinstalledfromhdd said:**
> Do you really want to install it that way?

Do a search on the following page for Netbeans to install it from the command line:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

With
> sudo apt-get install netbeans
I install NetBeans 6.9, but I want 7.0 ...

---

### Post by linuxinstalledfromhdd on 2011-05-29
Did you install the netbeans PPA?

[https://launchpad.net/ubuntu/+ppas?name_filter=netbeans](https://launchpad.net/ubuntu/+ppas?name_filter=netbeans)

---

### Post by redearth on 2011-07-10
This as a joke, no criticism intended, but did you try [checking that there is a netbeans ppa that includes version 7.0 before posting that link]("http://www.google.com/webhp?nord=1#sclient=psy&q=checking%20that%20there%20is%20a%20netbeans%20ppa%20that%20includes%20version%207.0%20before%20posting%20a%20link")?

(I wasn't able to find any, but I likely won't be of much help, either.) =) 

The installation bash script worked for me. So since there wasn't much info on your setup, I can only say:

1. Make sure you've updated Java alternatives to the JDK you want (e.g. 6.0.26).

2. Make sure you've set one of the following environment variables and have the path correctly set up, as the script expects:

POSSIBLE_JAVA_ENV="JAVA:JAVA_HOME:JAVAHOME:JAVA_PATH:JAVAPATH:JDK:JDK_HOME:JDKHOME:ANT_JAVA:"

POSSIBLE_JAVA_EXE_SUFFIX_COMMON="bin/java:"

---

### Post by Gyokuro on 2011-07-11
I can only recommend readearth's suggestions as Netbeans can be installed without any problems on Ubuntu with a proper JDK setup.

---

