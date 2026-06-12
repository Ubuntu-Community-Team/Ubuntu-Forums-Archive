---
title: "Help please: Linux installation problems and freeze/crash problem"
date: 2010-06-28
forum: General Help
---

### Post by Zihuatanejo on 2010-06-28
Hi everyone,

First time poster, relatively novice user!

Have dabbled a bit in Ubuntu for the last year or so, but have been somewhat held back by the fact that it simply doesn't seem to support three of the systems that I have installed it (or tried to install it) to.

I'll try to be concise; I have an aging desktop system (Alienware, Asus A8N mobo, 1Gb DDR400, Athlon XP3200+). My fiancée has an old HP Satellite laptop, I cannot recall the spec. At work I recently bought a Foxconn R10-S3 barebones system - [https://www.targetsecure.co.uk/newtc24/default.asp?vendor=&MenuId=&Prod=PBFOX-R10-S3++++](https://www.targetsecure.co.uk/newtc24/default.asp?vendor=&MenuId=&Prod=PBFOX-R10-S3++++)

The install process for my desktop and the laptop simply does not complete. I think this must be due to hardware conflicts. It is incredible frustrating. This is for 10.04 btw. I had problems with 9.10 on my desktop as well, enough that I simply gave up.

On the Foxconn system, i'm experience what my research seems to indicate to be a common problem - it just freezes/locks up after a few minutes of use. Not just keyboard/mouse freeze, but total (tried t oget something running in the background, then monitored, and the background process froze as well when the keyboard and mouse stopped responding). This is particularly annoying, as I'm sure you can imagine.

I was going to try Kubuntu and/or other Linux distros but haven't got around to downloading them yet.

I am quite experienced with computers/Windows, studied programming at university, run my own IT business, so I have probably tried the basic things. I am very new to Linux though.

I think that is about it. I also experienced the freezing problem on another laptop that belonged to a customer. Would have liked to have installed it on his laptop and replace Vista, which was causing him problems, but it froze after a few minutes. Useless :/

How can I go about running diagnostics to determine the cause and perform some sort of custom installation that eliminates the module (or whatever) that is causing the problem?

Many thanks in advance for your responses. I really need help on this one. I have researched it online and looked at similar threads, but couldn't find anythign relevant and basically have reached the point where I want to ask for help.

---

### Post by nacho32 on 2010-06-28
after reading your post I have to believe it sounds like a hardware problem and not a OS problem. What are the temps of the units running at? try swamping the ram out one stick at a time. I have installed Ubuntu back when it was 6 version something and more or less if the PC acceppted windows it would exceppt Ubuntu never had a conflicted, so I would check the hardware, you might want to try a older version on the older units.

---

### Post by Zihuatanejo on 2010-06-29
Hi Nacho, thanks for your reply.

All three of these machines have Windows XP running on them; nice and smooth, no problems.

So I'm sure it must be some sort of bizarre conflict between hardware and Ubuntu. Some sort of combination it doesn't like. I dunno :/

I may try an older version on my desktop and the laptop. How far back should I go? I'd really rather not though.

It is very frustrating!

---

### Post by dino99 on 2010-06-29
check that driver(s) is/are activated (system admin hardware driver

you might find usefull errors logged into .xsession-errors (/home, ctrl+h) and into: system admin logviewer

to see the verbose boot process (and conflicts if any), edit the boot line and remove: quiet splash then boot (if you dont see grub menu, at end of bios process, hold "shift" key down to see it)

---

### Post by Zihuatanejo on 2010-06-29
Thanks dino, I'll try and do that today and will post results.

---

### Post by Zihuatanejo on 2010-06-29
It is very difficult to troubleshoot this issue when you only have a two or three minute window in which to run commands and gather data!

No proprietary hardware drivers are in use, apparently..

I read on a forum thread somewhere to edit a grub config file in order to remove the 'quiet' and 'splash' options from boot menu, to see if it shows any relevant info during start up.

The command I was given was:

gksu gedit /boot/grub/menu.list

But i checked and menu.list does not exist in that folder. Is that a file to do with previous version of GRUB? I believe I am using GRUB2. If you could provide me with the command to do that, that'd be handy! I'll try and edit it through the BIOS as you suggested, just read that part again.

I can load log file viewer but I'm not sure how to view xsession-errors?


Thanks for your help so far, it is greatly appreciated.

---

### Post by vel. on 2010-06-29
> **Zihuatanejo said:**
> Hi Nacho, thanks for your reply.

All three of these machines have Windows XP running on them; nice and smooth, no problems.

So I'm sure it must be some sort of bizarre conflict between hardware and Ubuntu. Some sort of combination it doesn't like. I dunno :/

I may try an older version on my desktop and the laptop. How far back should I go? I'd really rather not though.

It is very frustrating!

Are you installing ubuntu linux from a CD/ DVD ? 
It might be a corrupted burn have you tried installing it from a new CD or just a USB drive?

---

### Post by forestG on 2010-06-29
> **Zihuatanejo said:**
> Thanks dino, I'll try and do that today and will post results.

Stupid thought but maybe the image of the cd you downloaded had flaws. Happens sometimes did you check the md5 sum?

[http://www.google.com/search?client=ubuntu&channel=fs&q=check+md5+sum&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=check+md5+sum&ie=utf-8&oe=utf-8)

---

### Post by the8thstar on 2010-06-29
+1 to the 2 previous posts. A faulty disc could be the cause of your problems.

---

### Post by the8thstar on 2010-06-29
> **Zihuatanejo said:**
> I read on a forum thread somewhere to edit a grub config file in order to remove the 'quiet' and 'splash' options from boot menu, to see if it shows any relevant info during start up.

The command I was given was:

gksu gedit /boot/grub/menu.list

But i checked and menu.list does not exist in that folder. Is that a file to do with previous version of GRUB? I believe I am using GRUB2. If you could provide me with the command to do that, that'd be handy! I'll try and edit it through the BIOS as you suggested, just read that part again.

That command is irrelevant since Ubuntu 10.04 relies on Grub2, which itself refers to a different set of files. Go here for more info on how to set Grub2 : [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by balasurfs on 2010-06-29
First, try to run a live CD on the problem machine. See if you are facing any problem. If live CD persists for a longer time, then we will move on to the next torubleshooting step.

Disable your HDD in bios, install the operating system you are looking for in a pendrive. Then try to boot it from pendrive. Most of the linux OS boot and run smoothly from pendrive. See if the system freezes again.

If the system is not freezing, then the problem can be with the HDD or the data cable connecting HDD to the motherboard. If it again freezes, the problem can be because of over heating or there are other things to discuss.

Thanks.

---

### Post by Zihuatanejo on 2010-06-29
D'oh, I should have thought of that. I burnt it to a DVD and I also created a bootable USB stick, can't remember which i used for which machine.

I will try burning the .iso again, nice and slow, and try and reinstall. Which is better to install from in terms of the likelihood of errors: USB stick or optical disc?

I'll do a md5 checksum as well. With Ubuntu 9, it had an option to 'check the disc for errors', which I always did when I burnt a new disc, but it seems to have disappeared from Ubuntu 10?

I'll keep you posted!

---

