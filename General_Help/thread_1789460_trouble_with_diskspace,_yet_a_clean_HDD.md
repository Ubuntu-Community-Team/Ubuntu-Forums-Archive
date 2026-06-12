---
title: "trouble with diskspace, yet a clean HDD??"
date: 2011-06-23
forum: General Help
---

### Post by matty4203 on 2011-06-23
is anyone else having trouble with their HDD's? i keep on getting messages claiming i only have 100mb of space yet, when i have something stupid like 250gb in reality, would appreciate any feedback/help :)

---

### Post by matty4203 on 2011-06-23
oh and to add to this, the file [/] claims to have 128.0 TB of data in there, despite it being a default folder?? brb, while i rip all of my hair out

---

### Post by haqking on 2011-06-23
> **matty4203 said:**
> oh and to add to this, the file [/] claims to have 128.0 TB of data in there, despite it being a default folder?? brb, while i rip all of my hair out

Well if you have installed ubuntu all into the default which is the root or / and havent created any other mount points then your whole linux system is in root or /

I doubt very much you have 128 TB of anything be it free space or not ? LOL but who knows you might work for the google or facebook or you use raw images in adobe...LOL

anyways, if everything is installed into one mount point of / then it is easy to run out of space if you didnt make / big enough when you installed.

which is possibly why you are getting the message about running out ?

upload a image of your filesytems from systems monitor or from Gparted to show us your disk configuration

---

### Post by matty4203 on 2011-06-23
aah found the problem of the 128.0Tb curse! [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/585472](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/585472)
and this is a wubi install of ubuntu, does that affect anything to do with HDD space?

---

### Post by haqking on 2011-06-23
> **matty4203 said:**
> aah found the problem of the 128.0Tb curse! [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/585472](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/585472)
and this is a wubi install of ubuntu, does that affect anything to do with HDD space?

ahh good, yes everything you install effects hard drive space, your install only be as large as the space provided on install whether it is Wubi or not.

You can use tools to change things later in most instances but for the most part you make sure at the beginning you have enough for your needs.

as we use to say in the army which equally applies to Linux is the 7 P's (Proper planning and preparation prevents p*** poor performance) :-)

at least you got the 128TB thing sorted, i was gonna say, thats plenty of space...LOL

---

### Post by dFlyer on 2011-06-23
Are you running wubi? There is another thread going about lost disk space, it turns out he was running wubi and max out the limited disk space wubi allows.

---

### Post by wildmanne39 on 2011-06-23
> **matty4203 said:**
> is anyone else having trouble with their HDD's? i keep on getting messages claiming i only have 100mb of space yet, when i have something stupid like 250gb in reality, would appreciate any feedback/help :)Hi, I suspected you install with wubi, I think it only allocates 8 gigs for the partition, because it is only meant for testing to see if you like ubuntu, then you can install it noramally. I am going to give you some links one is for making your partition larger in wubi, and the other is for turning your wubi install to a normal install just in case you decide you want too.
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

