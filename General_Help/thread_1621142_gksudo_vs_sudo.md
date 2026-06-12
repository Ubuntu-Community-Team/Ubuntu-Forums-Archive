---
title: "gksudo vs sudo"
date: 2010-11-13
forum: General Help
---

### Post by Monotoko on 2010-11-13
Hi there,

I always thought that gksudo was just a front-end to sudo, so that you didn't need to emulate the terminal to run it. It therefore uses less system resources etc. I have been told not using it is bad practise and it should **_ALWAYS_** be used when using graphical applications...but I do not understand how this is the case?

I will be honest, when I need to run something as root I run it under sudo...it has caused me no issues since Ubuntu 7.04.

---

### Post by Decatf on 2010-11-13
[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)

---

### Post by Monotoko on 2010-11-13
I have read that, but surely that is only for applications in your home dir to begin with?

If I am running, for example, gparted surely it doesn't matter?

---

### Post by qamelian on 2010-11-13
> **Monotoko said:**
> I have read that, but surely that is only for applications in your home dir to begin with?

If I am running, for example, gparted surely it doesn't matter?
Whether or not there will be a problem depends on the individual app. Rather than trying to remember which apps may be affected, it is just simpler to always use gksu/gksudo for graphical apps as you are intended to do.

---

### Post by yetiman64 on 2010-11-13
> **Monotoko said:**
> I have read that, but surely that is only for applications in your home dir to begin with?

If I am running, for example, gparted surely it doesn't matter?
Have a read of this link,
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

>   **Why is it an issue?**
Well, to be perfectly honest, most of the time it isn't. For a lot of applications, you can run them the improper way—using *sudo* for graphical applications and see no adverse side effects. 
 1. There are other times, though, when side effects can be as mild as [[COLOR=Blue]Firefox extensions not sticking[/COLOR]]("http://ubuntuforums.org/showthread.php?t=201488") or as extreme [[COLOR=Blue]as not being able to log in any more because the permissions on your .ICEauthority changed[/COLOR]]("http://ubuntuforums.org/showthread.php?t=181867"). You can read a full discussion on the issue [here]("http://www.mail-archive.com/arch@archlinux.org/msg04963.html"). 
 These errors occur because **sometimes when *sudo* launches an application, it launches with root privileges but uses the user's configuration file. **
Last sentence bolded for emphasis. Read the links included in the above quote for situations where using sudo has caused problems.

It is far easier/more convenient to remember **gksudo = graphical applications** and **sudo = terminal applications**, rather than trying to maintain a comprehensive list of applications that are safe to use with sudo.

---

