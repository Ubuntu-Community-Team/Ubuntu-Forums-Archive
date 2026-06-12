---
title: "University Assignment First time help."
date: 2010-05-16
forum: General Help
---

### Post by Werner7 on 2010-05-16
Hey everyone,

Forgive me for not contributing to other posts before asking for help. This is due to not knowing Linux good enough.

I just need leadership in what to do for a university assignment I got. 

It is to dual boot Ubuntu with Windows. And then the more things we do with the installation (like installing 3 OS's or running some advanced scripts or just do something advanced with Ubuntu the higher marks we get. I'd like to get A+ for this one. :)
(I know how to install, dual boot and all the setup of the desktop version of Ubuntu)

So i want to install Ubuntu on 2 PCs. One being the server and other one the client. Can i use the Ubuntu desktop version to run as a server? Or should i really go for the Server version?
I'm still fairly new to Linux, so command line isn't my strong point. What options is there? 

Thanks.

---

### Post by kevinatkins on 2010-05-16
Hello!

Sounds like quite a nice assignment you've got there actually - should be fun.

Let's take things a step at a time though..

Dual boot Ubuntu with Windows - dead easy. Make sure you've got Windows installed first, then just pop in an Ubuntu CD and go from there - it will walk you through it.

Triple boot - that's a bit more complicated.. but not hugely difficult. Be aware that the latest versions of Ubuntu (since 9.10 I think) use the Grub 2 boot loader, which is somewhat different to earlier versions, so the detail of many tutorials on the net will be out of date. You will need to get involved with boot loaders if you're doing fancy multiple boots, so if you want the broadest tutorial support from the net, I'd suggest choosing an earlier version of Ubuntu (eg, 8.04)

Server / client question - the big difference between the Ubuntu server and desktop versions is that the server version doesn't install a windowing system by default - it just operates in text mode. But there's absolutely nothing to stop you installing and running various server apps on a desktop installation (eg, Apache, BIND, etc..) But you specifically mention a server / client type of installation, which suggests a Linux Terminal Server Project (LTSP) type of configuration, which Ubuntu supports - eg, low power clients connect to server, with full GUI etc. I have no experience of that, but you might want to look at Edubuntu, and google Ubuntu LTSP for ideas....

---

### Post by Werner7 on 2010-05-16
> **kevinatkins said:**
> Hello!

Sounds like quite a nice assignment you've got there actually - should be fun.

Let's take things a step at a time though..

Dual boot Ubuntu with Windows - dead easy. Make sure you've got Windows installed first, then just pop in an Ubuntu CD and go from there - it will walk you through it.

Triple boot - that's a bit more complicated.. but not hugely difficult. Be aware that the latest versions of Ubuntu (since 9.10 I think) use the Grub 2 boot loader, which is somewhat different to earlier versions, so the detail of many tutorials on the net will be out of date. You will need to get involved with boot loaders if you're doing fancy multiple boots, so if you want the broadest tutorial support from the net, I'd suggest choosing an earlier version of Ubuntu (eg, 8.04)

Server / client question - the big difference between the Ubuntu server and desktop versions is that the server version doesn't install a windowing system by default - it just operates in text mode. But there's absolutely nothing to stop you installing and running various server apps on a desktop installation (eg, Apache, BIND, etc..) But you specifically mention a server / client type of installation, which suggests a Linux Terminal Server Project (LTSP) type of configuration, which Ubuntu supports - eg, low power clients connect to server, with full GUI etc. I have no experience of that, but you might want to look at Edubuntu, and google Ubuntu LTSP for ideas....

Thanks for that, i will look into that. Yea, I'm also required to modify GRUB, So im guessing there will be tools out there for GRUB 2 already? If not, then editing the file could be done I'm sure.

---

### Post by Ozymandias_117 on 2010-05-16
> **Werner7 said:**
> Thanks for that, i will look into that. Yea, I'm also required to modify GRUB, So im guessing there will be tools out there for GRUB 2 already? If not, then editing the file could be done I'm sure.
A very, very good tutorial on Grub 2:
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by Werner7 on 2010-05-16
> **Ozymandias_117 said:**
> A very, very good tutorial on Grub 2:
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

Ah thanks for that, that got bookmarked. Its going to become very handy thanks. :D

---

### Post by eltonw on 2010-05-16
> **Werner7 said:**
> Ah thanks for that, that got bookmarked. Its going to become very handy thanks. :D

You may find some useful links to help in learning more linux basics, etc:
[http://ubuntuforums.org/showthread.php?t=1483371]("http://ubuntuforums.org/showthread.php?t=1483371")

respectfully

---

### Post by Werner7 on 2010-05-16
> **eltonw said:**
> You may find some useful links to help in learning more linux basics, etc:
[http://ubuntuforums.org/showthread.php?t=1483371]("http://ubuntuforums.org/showthread.php?t=1483371")

respectfully

sweet, thanks for that. Another page bookmarked! I love Ubuntu, just i like gaming too. So i'll be a full on supporter for steam when they release their Linux version. Which should launch this year or early next.

---

### Post by Ozymandias_117 on 2010-05-16
> **Werner7 said:**
> sweet, thanks for that. Another page bookmarked! I love Ubuntu, just i like gaming too. So i'll be a full on supporter for steam when they release their Linux version. Which should launch this year or early next.

Where did you find this information??

---

### Post by Werner7 on 2010-05-17
> **Ozymandias_117 said:**
> Where did you find this information??

Various places although the people with most information that i know of is [phoronix]("http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1")

The Title goes "It's Official: Valve Releasing Steam, Source Engine For Linux!"  - 12 May 2010

They also did a test on another post on phoronix on OpenGL perfomance compared with Windows 7, OS X, and Ubuntu 10.04.

Windows took a slight lead over Ubuntu, however Mac was far behind.

This is enough to make gamers who would like to go on Linux excited. One thing will lead to the other.

---

