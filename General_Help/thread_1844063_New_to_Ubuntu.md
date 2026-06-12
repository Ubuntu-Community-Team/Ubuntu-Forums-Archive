---
title: "New to Ubuntu"
date: 2011-09-14
forum: General Help
---

### Post by Jiggle156 on 2011-09-14
I finally managed to set my Ubuntu up properly - loving it so far. I have a couple of questions though:
1) Is it safe for me to download and install adobe flash player? Apparently it's packed with security leaks etc.
If not - could anyone recommend a reasonable alternative?
2) Where would be a good site to learn about the ins and outs of using Ubuntu, how to stay secure, and how to use the terminal? 

Thanks in advance ;D

---

### Post by haqking on 2011-09-14
> **Jiggle156 said:**
> I finally managed to set my Ubuntu up properly - loving it so far. I have a couple of questions though:
1) Is it safe for me to download and install adobe flash player? Apparently it's packed with security leaks etc.
If not - could anyone recommend a reasonable alternative?
2) Where would be a good site to learn about the ins and outs of using Ubuntu, how to stay secure, and how to use the terminal? 

Thanks in advance ;D


1. For flash i suggest using [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/") as it will download most appropriate for your system and be used across the system.

2. Linux can be daunting due to unfamiliar terrritory but to become a confident user only comes only with experience and read, read, read and try, try try then there are at least some basics needed.

First of all i suggest getting to get grips with the security model early on, as there is alot of misunderstanding about Viruses in Linux and malware in general etc so i refer you first to the importance of using sudo here at:

**Security**

rootsudo **(very important you read this one)**
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

here for security in general

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

and these stickies (in my signature)

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

here for virus information

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

You might also want to look at Tor for anonymizing your connection:
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Firewalls are not generally needed on a home desktop machine as that is taken care of by your router however there is a hardcoded firewall in Linux called Netfilter/IPTables and can be configured by reading here:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Though most people if use anything use UFW/GUFW which is a interface for managing IPTables without the complicated command line. see here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Also look at apparmor for profiling your applications and there privelege:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

and this will give you a good grounding in the security of your system and such like.

**Virtualisation and testing**

After that it is a case of play, setup virtual machines so you can play without trashing your machine, see:

[www.virtualbox.org]("http://www.virtualbox.org")

and this sub-forum [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

that way you can play with partitions and CLI etc without risking anything.

**Command Line (terminal)**


[https://help.ubuntu.com/community/Be.../BashScripting](https://help.ubuntu.com/community/Be.../BashScripting)

[http://linuxcommand.org/](http://linuxcommand.org/)

**Apps and Games  and Productivity**

Then it comes down to what you want do and achieve, try the following for a starter:

[http://www.makeuseof.com/tag/10-appl...tu-lucid-lynx/](http://www.makeuseof.com/tag/10-appl...tu-lucid-lynx/)
[http://blog.sudobits.com/2011/03/19/top-10-ubuntu-apps/](http://blog.sudobits.com/2011/03/19/top-10-ubuntu-apps/)
[http://blog.sudobits.com/2011/03/07/...-ubuntu-games/](http://blog.sudobits.com/2011/03/07/...-ubuntu-games/)

There is so much, it is a case of where do you start.

These are mainly Desktop related, but you may also need or want to look at servers and services so here is a good read:
[B]
Server and Services[/B]

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)


Have fun

Regards

haqking

---

### Post by wolfen69 on 2011-09-14
> **Jiggle156 said:**
> I finally managed to set my Ubuntu up properly - loving it so far. I have a couple of questions though:
1) Is it safe for me to download and install adobe flash player? Apparently it's packed with security leaks etc.
If not - could anyone recommend a reasonable alternative?
Any alternative is garbage. As a flash user of many years, I've never experienced any issues with it.
> 2) Where would be a good site to learn about the ins and outs of using Ubuntu, how to stay secure, and how to use the terminal? 

Thanks in advance ;D
[www.ubuntuguide.org](www.ubuntuguide.org) is a good site. Also, for the terminal, there's [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) among many others. Let google be your friend.

---

### Post by Frogs Hair on 2011-09-14
(Command Line)

[http://linuxcommand.org/](http://linuxcommand.org/)

[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

[http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

[http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/)

---

### Post by Jiggle156 on 2011-09-14
Well, thank-you all for the speedy replies! I'll have plenty of reading around to do in order to understand some of this stuff, but hopefully I will come out the other end with a better understanding of Ubuntu :)  Some of the security-related applications seem complicated to use, like I.P tables, for someone that doesn't fully understand it.

---

### Post by haqking on 2011-09-14
> **Jiggle156 said:**
> Well, thank-you all for the speedy replies! I'll have plenty of reading around to do in order to understand some of this stuff, but hopefully I will come out the other end with a better understanding of Ubuntu :)  Some of the security-related applications seem complicated to use, like I.P tables, for someone that doesn't fully understand it.


Dont worry too much about that.  IPTables refers to the firewall built into the kernel, which you can configure from CLI or with interfaces such as UFW.GUFW, Firestarter etc.

However Linux comes with no ports open by default so using a firewall is of no benefit as to not using one.

If you enable services then you might considier it, but most home users are protected by their router anyways and the only thing you need to do is port forward the services through to your machine.

So dont worry too much, but the biggest security flaw in any system is the user, so worry a little ;-)

And dont do silly things !

make sure you read the [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo") link i posted though, make sure you fully understand it and its usage.

---

### Post by Jiggle156 on 2011-09-14
A quick afterthought - is having a windows partition on my HDD a security risk? I will have no second thought about removing it, if it is xD

---

### Post by haqking on 2011-09-14
> **Jiggle156 said:**
> A quick afterthought - is having a windows partition on my HDD a security risk? I will have no second thought about removing it, if it is xD


NO not really.  If you share files with windows users from your linux system then you might need Av of some description, but that is all covered in the AV links above i posted.

---

