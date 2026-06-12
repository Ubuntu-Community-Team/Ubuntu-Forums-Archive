---
title: "Cannot see capthas in Natty"
date: 2011-05-24
forum: General Help
---

### Post by frank cox on 2011-05-24
I love Ubuntu and Linux in general but Java wears me out. When I want to register for a newsgroup or what ever and it asks to type in the letters they are not there.  Having to switch distros every time I need to do that is getting old. Any help would be appreciated.

Sometimes I think webmasters are self centered. If they considered the fact that not everybody can see these capthas they would just ask a math question or whatever to fool the spam bots.

---

### Post by 5149.5 on 2011-05-24
There are 2 versions of java and a couple of ways of getting each. The easiest way is to open software center and loading the Icedtea plugin for browsers.

---

### Post by frank cox on 2011-05-24
> **5149.5 said:**
> There are 2 versions of java and a couple of ways of getting each. The easiest way is to open software center and loading the Icedtea plugin for browsers.

I loaded java runtime from the command line, do I need to remove it to install Icedtea?

---

### Post by 5149.5 on 2011-05-24
I just looked at synaptic and I'm guessing that when you say java runtime, you are talking about jre(java runtime environment). That is just another version of java and it should work just as well. Doesn't that one work for you?

---

### Post by ajgreeny on 2011-05-24
I suggest you install sun-java6 versions of the java apps you need; they are all in the canonical partner repositories in 10.04, but I'm not sure where in natty, and whilst it would be nice to be able to use open source versions of java, they do not always seem to work in all websites.

Sun-java6 always does in my experience.

---

### Post by frank cox on 2011-05-24
> **5149.5 said:**
> I just looked at synaptic and I'm guessing that when you say java runtime, you are talking about jre(java runtime environment). That is just another version of java and it should work just as well. Doesn't that one work for you?

It works sometime , the biggest problem is it rarely sees capthas.

---

### Post by linuxinstalledfromhdd on 2011-05-24
This is a nice guide for getting all the basics installed on your system. I highly suggested that you try this first. Java is about half the way through the list.  It is very helpful. :P

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by frank cox on 2011-05-24
I removed the Java that was there and installed sunjava but it still says iced tea 

Setting up sun-java6-plugin (6.25-1~lffl) ...
User@User-Inspiron-530:~$ java -version
java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.1) (6b22-1.10.1-0ubuntu1)
OpenJDK Server VM (build 20.0-b11, mixed mode)
User@User-Inspiron-530:~$

---

### Post by linuxinstalledfromhdd on 2011-05-25
Did you try the guide yet?

---

### Post by wildmanne39 on 2011-05-25
> **frank cox said:**
> I removed the Java that was there and installed sunjava but it still says iced tea 

Setting up sun-java6-plugin (6.25-1~lffl) ...
User@User-Inspiron-530:~$ java -version
java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.1) (6b22-1.10.1-0ubuntu1)
OpenJDK Server VM (build 20.0-b11, mixed mode)
User@User-Inspiron-530:~$
Hi, use 
```
sudo apt-get --purge remove package name
```to remove all ice tea if you can not get rid of it, also you probably need to use that command to get rid of all the old config files left behind by installing and removing java. After you remove restart your computer then install java just to be sure.

---

### Post by frank cox on 2011-05-25
thanks

---

