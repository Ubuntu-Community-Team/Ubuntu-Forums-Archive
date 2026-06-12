---
title: "Can you help a coding noob? And specifically with building the RT3090 PCIe driver?"
date: 2010-08-18
forum: General Help
---

### Post by MrHarryWarne on 2010-08-18
**[If you're confused by the name of the wireless card, please read my edit at the bottom of the post.]**

Right, I'm new to the whole Linux world. And also to coding and the general use of tools like Terminal. To highlight just how much of a noob I am: the other day I was really chuffed with myself for learning how to eject my USB drive in OSX using *diskutil eject /dev/disk1/* , or something like that. So I guess that gives you an idea of my skill level.

Ok, so the root of my problem is trying to get drivers for a RaLink RT3090 PCIe wireless card inside of some crappy netbook that hasn't even got the model name on it. It's my ex-girlfriend's, she bought it from the clothes shop Next. I knew I should've advised her against it. She managed to mess up XP pretty bad about a week ago. So she asked me for help. I had a look and XP was well and truly screwed. Fixing it would've involved techniques that I just don't know how to do. I'd begun looking at Ubuntu as a 3rd partition on my MacBook Pro, and though "Aha! Why not install Ubuntu 10.04 Netbook Remix via USB onto her netbook. It will be easy!" I installed it fine, but now it's gotten to the stage of hunting around for drivers, I feel I've reached the limit of my knowledge.

There are many threads on this site dealing with the RT3090, and many of them give solutions and have people posting thank you replies saying that they worked. The only problem is, these solutions give long strands of code and what not. You wouldn't think this would be a problem because I should be able to just follow step by step. Well what trips me up is the use of terminology and shorthand. For instance, I will quote from a readme that came with the latest RT3090 drivers, in the section detailing how to build the driver from the included files:

```
1> $tar -xvzf DPB_RT2860_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2860_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.
```

Now I'm sure to a lot of people on this forum this will look idiot proof, but for me I have no idea. For instance: 'x.x.x.x.tgz' and '...x.x.x.x." directory.' What am I supposed to replace 'x.x.x.x.' with? And 'set the "MODE = STA" in Makefile and chose [*choose?] the TARGET to Linux...' What does any of that mean?!?!??!


So I'm asking two things:

1. Is there anywhere anyone can point me to learn these sort of things? (Preferably not involving purchasing anything.) How did everyone else come to understand all these things, as well as general Terminal tasks?

2. Can anyone help me specifically with building the RT3090 PCIe driver, bearing in mind this level of computing is new to me.

I'm not a complete idiot when it comes to computers, but this is the first time I've ever really delved into the world of Linux and coding generally. I want to learn, but for the time being, I'm in slightly too deep. (And my ex wants her laptop back, xD.)


Thank you so much in advance, I've been at this for literally days and have gotten no where.

EDIT: OK, just to confuse me more...when I use: ```
sudo lshw -c network
``` it tells me I have an RT3090 PCIe. But when I use: ```
iwconfig
``` it tells me that I have an RT2860 Wireless ESSID. Wth?!

---

