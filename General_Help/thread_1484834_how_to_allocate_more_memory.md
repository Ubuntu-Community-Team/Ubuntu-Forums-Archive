---
title: "how to allocate more memory"
date: 2010-05-16
forum: General Help
---

### Post by shibby4555 on 2010-05-16
hey all,
i just recently installed ubuntu 10.04 onto my laptop. its running as a dual boot. i only allocated about 10gb of memory and have already run out. is it possible to allocate more memory afterwards

and another bug that i am having is my shift key is not functioning properly. if anyone happens to know this issue too. so i can't do exclamations of periods, capitalizations, etc... how would you remap your keyboard

thanks in advance for the help. i'm not very good at computers, so if you can use simplistic terms,
thanks guys
-shibby

---

### Post by Bachstelze on 2010-05-16
> **shibby4555 said:**
> hey all,
i just recently installed ubuntu 10.04 onto my laptop. its running as a dual boot. i only allocated about 10gb of memory and have already run out. is it possible to allocate more memory afterwards

Yes, you can boot a Live CD and use GParted to modify your partitions. This is not without risk for your data, though, so you should backup your important files first.

---

### Post by brethren on 2010-05-16
system->preferences->keyboard

---

### Post by shibby4555 on 2010-05-16
thanks

---

### Post by life in color on 2011-06-05
I installed Ubuntu using Wubi and I am now dual booting Windows and Ubuntu. I was a bit confused when I first installed Ubuntu and only allocated the default 17gb of memory for Ubuntu. I figured I could just use GPARTED to resize the partitions but I came to find out that Windows and Ubuntu are on the same partition, I don't know what I should do....any help?

---

### Post by Mark Phelps on 2011-06-06
First of all, let's get the terms right ... it's not MEMORY, it's Disk Space.

Second, since it was a Wubi install, it did not use traditional partitioning -- so you can't use that approach to increase the allocated Disk Space.

See the Wubi Guide linked below, section 8.9 for details:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by life in color on 2011-06-06
@Mark Phelps (sorry for the twitter/youtube style reply) yes sorry about that I realize memory = RAM etc. anyhow I'm considering just deleting ubuntu and then making a live CD and re-installing it, would this be a good idea? If not I can follow the instructions for transferring it to a new partition I'm just afraid I may make a fatal error as I'm a beginner with Linux.

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **life in color said:**
> @Mark Phelps (sorry for the twitter/youtube style reply) yes sorry about that I realize memory = RAM etc. anyhow I'm considering just deleting ubuntu and then making a live CD and re-installing it, would this be a good idea? If not I can follow the instructions for transferring it to a new partition I'm just afraid I may make a fatal error as I'm a beginner with Linux.

The best way to go would be a live Ubuntu USB Flash drive installation.. installation is much faster that way too.

Here is a nice walkthrough for new users..  Try 10.10 first, since that was the last fully tested version of Ubuntu. 

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

