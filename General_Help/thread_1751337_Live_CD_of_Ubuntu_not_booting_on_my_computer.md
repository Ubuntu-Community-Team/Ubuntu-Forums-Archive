---
title: "Live CD of Ubuntu not booting on my computer"
date: 2011-05-06
forum: General Help
---

### Post by Thecoolguru on 2011-05-06
Hello everyone.

So I have an old laptop with a copy of CrunchBang Linux installed in one of its partitions. I want to try out the latest Ubuntu release, so I went to make a Live CD so I could take a look at it and use a GUI installer. I downloaded the i386 ISO file, checked the md5sum (it matched), and proceeded to burn my CD. My burning application checked to verify that the data had been burned properly, and it had. So I popped it into my CD drive, turned on my computer, and selected to boot from the CD drive. I had the blinking cursor at the top left of the screen that I always get when I first boot anything from CD, but it stayed there for a solid 15 seconds. Then it proceeded to boot from my hard drive. I had this problem once with an Ubuntu Live CD before, but I know that this computer can boot CDs. I used to have Ubuntu installed on my computer (back in the days of Gutsy), and it worked fine. Any ideas on what the culprit might be?

Thanks in advance,
thecoolguru

EDIT: I just tested the CD on my new computer (the one I want to install it on is somewhere between 7-10 years old), and it booted fine. Does Natty have some sort of bug where it can't support old computers?

---

### Post by FlyingUnderTheRadar on 2011-05-25
Many people are having the same problem with Ubuntu 11.04.
I cannt boot a Ubuntu Live CD (32 or 64 bit) from a 2010 Mac Mini (bootcamp), 2010 Macbook Pro 13" (bootcamp), 2011 Macbook Pro 17" (bootcamp) or VMware Fusion 3.1.

Try a different distribution of LINUX such as Debian for now. 
Their downloads are pretty fast and extensive.

---

### Post by wildmanne39 on 2011-05-25
> **Thecoolguru said:**
> Hello everyone.

So I have an old laptop with a copy of CrunchBang Linux installed in one of its partitions. I want to try out the latest Ubuntu release, so I went to make a Live CD so I could take a look at it and use a GUI installer. I downloaded the i386 ISO file, checked the md5sum (it matched), and proceeded to burn my CD. My burning application checked to verify that the data had been burned properly, and it had. So I popped it into my CD drive, turned on my computer, and selected to boot from the CD drive. I had the blinking cursor at the top left of the screen that I always get when I first boot anything from CD, but it stayed there for a solid 15 seconds. Then it proceeded to boot from my hard drive. I had this problem once with an Ubuntu Live CD before, but I know that this computer can boot CDs. I used to have Ubuntu installed on my computer (back in the days of Gutsy), and it worked fine. Any ideas on what the culprit might be?

Thanks in advance,
thecoolguru

EDIT: I just tested the CD on my new computer (the one I want to install it on is somewhere between 7-10 years old), and it booted fine. Does Natty have some sort of bug where it can't support old computers?
Hi, go into bios when you first turn your computer on, it will be like f8 or delete key something like that will get  you into bios, then select your cd to be the first boot device.

---

### Post by mindstorms83 on 2011-05-25
> **Thecoolguru said:**
> Hello everyone.

So I have an old laptop with a copy of CrunchBang Linux installed in one of its partitions. I want to try out the latest Ubuntu release, so I went to make a Live CD so I could take a look at it and use a GUI installer. I downloaded the i386 ISO file, checked the md5sum (it matched), and proceeded to burn my CD. My burning application checked to verify that the data had been burned properly, and it had. So I popped it into my CD drive, turned on my computer, and selected to boot from the CD drive. I had the blinking cursor at the top left of the screen that I always get when I first boot anything from CD, but it stayed there for a solid 15 seconds. Then it proceeded to boot from my hard drive. I had this problem once with an Ubuntu Live CD before, but I know that this computer can boot CDs. I used to have Ubuntu installed on my computer (back in the days of Gutsy), and it worked fine. Any ideas on what the culprit might be?

Thanks in advance,
thecoolguru

EDIT: I just tested the CD on my new computer (the one I want to install it on is somewhere between 7-10 years old), and it booted fine. Does Natty have some sort of bug where it can't support old computers?
I had sort of the same problem, my current computer is like 5-6 years old and it wouldn't boot Natty, then when I finally got it to, it wouldn't install, etc etc, However, I still had my windows partition, so I went and got the latest LTS version of ubuntu (10.04 Lucid Lynx) and made a Live Cd of it, installed, and then did the update manager upgrade to Ubuntu 10.10 Maverick meerkat. Last time I went to get the Natty .iso, the download version of Natty was still "Beta" So that could be the problem, I reccomend getting an older copy of Ubuntu (such as 10.04, 10.10) and trying that instead, also I would take wildmanne39's advice and look in the BIOS options of your computer, and then change the default boot order so that it boots from the CD to begin with, I would also check to see if you may have accidently burned th copy of Natty to a DVD, or a CD that is not supported by older optical disc drives, Good Luck!

---

