---
title: "New To Ubuntu"
date: 2012-02-25
forum: General Help
---

### Post by scottinpa40 on 2012-02-25
Hi everyone, I just had 2 quick questions for you.  I just used the Wubu installer on my Acer desktop PC with Windows 7 and everything went well with the install.  My first question...is there any disadvantages in using the Wubi installer and just having Ubuntu installed as a program in Windows that can be uninstalled?  My 2nd question is, how can I see my Windows files from my hard drive while using Ubuntu?  I have my hard drive partitioned...the part of the drive with Windows on it is Acer (C:) and I an able to see that on the Ubuntu screen.  The other part of the drive is DATA (D:) and I have Ubuntu installed on that, which I used Wubi to install it.  For some reason, I am unable to locate the D: drive, which has my music, pictures, etc.  Thanks for any help you can give me since I'm new to this!

-Scott

---

### Post by bcbc on 2012-02-25
The host partition (D: in your case) is mounted on /host 
You can get it with Alt-F2, /host and then Ctrl+D to bookmark in Nautilus. Otherwise open Nautilus (folder icon) and click on 'File System' and look for 'host'

Here's a post on the difference:
[http://askubuntu.com/questions/615/whats-the-difference-between-wubi-and-a-regular-installation](http://askubuntu.com/questions/615/whats-the-difference-between-wubi-and-a-regular-installation)

The biggest disadvantage is also Wubi's biggest advantage: having a virtual disk means you don't have to partition and it's simple to install/uninstall. But it also means that all your Ubuntu files are stored within a single file on the host partition. So, obviously if you deleted it or is was corrupted you could lose your Ubuntu install.

If your computer is hanging don't hard shutdown. Instead use [Alt+SysRq R-E-I-S-U-B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot") to safely reboot.

---

### Post by scottinpa40 on 2012-02-25
Thanks for your help!  I'm not exactly sure of what keys to press for the Alt+SysRq R-E-I-S-U-B that you mentioned.  Do you hit ALt+SysRq, then type R-E-I-S-U-B?

---

### Post by bcbc on 2012-02-25
From the link I posted (which I recommend reading as it helps to understand what it's doing):

> 1. Hold down the Alt and SysRq (Print Screen) keys.
2. While holding those down, type the following keys in order, several seconds apart: REISUB
3. Computer should reboot.

---

### Post by scottinpa40 on 2012-02-25
Thanks alot for your help!  I really appreciate it.

---

### Post by bcbc on 2012-02-26
> **scottinpa40 said:**
> Thanks alot for your help!  I really appreciate it.

You're welcome :)

---

