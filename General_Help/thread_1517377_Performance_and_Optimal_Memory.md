---
title: "Performance and Optimal Memory?"
date: 2010-06-25
forum: General Help
---

### Post by Ron O on 2010-06-25
Running Ubuntu Lucid on a desktop with 1 GB RAM. If I look into System Monitor I am generally using about 1/3 of the memory and seldom over half. And I have swappiness set to 10 so my swap file never seems to be in use. So it does not seem to me that I would get any performance gains by adding an additional gig of RAM, but I am not certain of this. 

After running 3 prior versions of Xubuntu, I find the general system responsiveness in Ubuntu a bit sluggish. Would I gain anything by installing more RAM?

---

### Post by d3v1150m471c on 2010-06-25
Not much if you're never doing anything to fill up your cache. You need a faster processor, truth be told.

---

### Post by Ron O on 2010-06-27
I thought a dual core at 2.8G per core was pretty respectable. This is Linux, not Windoze. I guess I got spoiled by Xubuntu, but I had installation problems with the new release and none with Ubuntu. I was also using the Preload daemon which seemed to speed things up a lot, but this program currently does not work with Lucid.

---

### Post by cascade9 on 2010-06-27
If you are not using all your RAM, in most cases, no, adding RAM will not help at all. The only time it will help is if you have a motherboard/chipset that supports dual-channelRAM and you are running in single channel mode. 

> **Ron O said:**
> After running 3 prior versions of Xubuntu, I find the general system responsiveness in Ubuntu a bit sluggish. Would I gain anything by installing more RAM?

Xubuntu isnt exactly fast. Try a minimal install ubuntu then add xfce, xorg and gdm (or xdm). Its noticably quicker ;)

---

### Post by keithpeter on 2010-06-27
> **Ron O said:**
> ...I find the general system responsiveness in Ubuntu a bit sluggish. Would I gain anything by installing more RAM?

I'm using stock Ubuntu Lucid on an Asus 2.4GHz per core dual core box with 874 Mb of ram available for the operating system (nvidia integrated graphics has the rest of the 1Gb stick allocated as video ram). 

Performance seems ok to me, and I'm using about a third of the available memory as well, not super fast but definitely not like molasses either.

What kinds of thing are taking longer than you think they should? What kind of video card do you have and what video settings have you got set?

---

### Post by efflandt on 2010-06-27
I suspect that it could be a video issue depending upon what hardware you have.  The new kernel mode setting (KMS) driver may not work well with certain hardware.

Certain things were sluggish with 10.04 on my desktop with ATI X1300 video and I was unable to go into suspend or hibernate.  The **nomodeset** kernel boot option restored it to 9.10 speed and fixed suspend/hibernate.  That also fixed a boot graphic glitch/hang on my work laptop with Radeon Mobility X1300.

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

---

### Post by Ron O on 2010-06-27
I've got a Visiontek video card that I believe is a Radeon 7000 and I am using the Ubuntu included drivers- I know this is part of the problem because this card flies in Windows. When I open Firefox, the upper left of the window leaves a 2" x 2" square of the desktop for a few seconds before it draws the rest of the Firefox window. But I cannot seem to find a proprietary Linux driver for it. The repositories don't have one and even Visiontek's site does not. But you would think there would be an ATI Linux driver somewhere that would run on this card. If it's possible to tweak the Ubuntu drivers, I don't know how to do it. 

The speed I am talking about is more what I think of as program execution speed. For example, if I run Rootkit Hunter in Terminal (scans system for rootkits/malware), it kind of lopes leisurely along while in Xubuntu it scrolls through so fast you can hardly read it.

Another thing I noticed with Ubuntu from System Monitor is that it NEVER utilizes the full potential of my processor- maybe 50% on one core and 50% of the 2d core at most. If I give the processor an intensive task in Windoze, like computing prime numbers, both cores run at 100%. I hate to keep refering to Windoze, because in all other respects I hate it and do not use it. But it does show that Ubuntu (or the Linux kernel) are not making use of the resources I have. I started a thread somewhere on the processor issue and never got a sensible answer.

---

### Post by wraithchild on 2010-06-29
Hi Guys thank god i found you! I'll start with my hardware.

XFX GeForce 8300 motherboard,
XFX GeForce GT220 1GB graphics card,
AMD Athlon 64 X2 5400 CPU @ 2.7ghz HT
2GB Corsiar Xtreme DDR2 - 800mhz Dual Channel Ram
320GB Barracuda HDD
Acer V193W 19" LCD monitor.

[IMG]http://linuxforums.org.uk/index.php?action=media;sa=media;in=542[/IMG]

My issue is that even when running idle by idle i mean only running Swiftfox browser and my custom Conky Desktop Hardware monitor, My CPU bounces up and down like a "Prostitutes knickers" and my Ram is back and forth at 700 - 800MB in use??? 

Why is the system so so so heavy on memory and CPU usage when its doing very little or nothing??? 

NB: This maybe nothing but my swap file is 4612MB and its not being used...

Cheers Wraithchild

---

### Post by cascade9 on 2010-06-29
@ wrathchild- odd, conky has your 'top processes' as xorg (2.45%) and compiz (2.14%) but you are using 19% on CPU1 and 21% on CPU2. So where the heck is the rest going? o.O 

I'd have a look in 'htop' and see wha other processes are using CPU. 

> **Ron O said:**
> I've got a Visiontek video card that I believe is a Radeon 7000 and I am using the Ubuntu included drivers- I know this is part of the problem because this card flies in Windows. When I open Firefox, the upper left of the window leaves a 2" x 2" square of the desktop for a few seconds before it draws the rest of the Firefox window. But I cannot seem to find a proprietary Linux driver for it. The repositories don't have one and even Visiontek's site does not. But you would think there would be an ATI Linux driver somewhere that would run on this card. If it's possible to tweak the Ubuntu drivers, I don't know how to do it. 

The 7000 series, and quite a few newer ATI cards no longer have ATI support. So no proprietary drivers are avaible. 

> **Ron O said:**
> The speed I am talking about is more what I think of as program execution speed. For example, if I run Rootkit Hunter in Terminal (scans system for rootkits/malware), it kind of lopes leisurely along while in Xubuntu it scrolls through so fast you can hardly read it.

Adding RAM will not help program execution speed if you arent using the majority of your RAM already. It will only help when you are using the swap drive (and its got to be quite a bit of use, not a few MB). 

> **Ron O said:**
> Another thing I noticed with Ubuntu from System Monitor is that it NEVER utilizes the full potential of my processor- maybe 50% on one core and 50% of the 2d core at most. If I give the processor an intensive task in Windoze, like computing prime numbers, both cores run at 100%. I hate to keep refering to Windoze, because in all other respects I hate it and do not use it. But it does show that Ubuntu (or the Linux kernel) are not making use of the resources I have. I started a thread somewhere on the processor issue and never got a sensible answer.

Probably you are using single-threaded only applications. If you try a program that is multithreaded, you should use both CPUs- try some video encoding program, like handbrake, dvdrip, k9copy, etc.

---

### Post by wraithchild on 2010-06-29
[IMG]http://farm5.static.flickr.com/4118/4745895999_b4f1108ce1_b.jpg[/IMG]


Sorry i've no idea what i'm specificaly looking for here but looks like /usr/bin/x and Gnome terminal are big contributors to the usage..???

---

### Post by Ron O on 2010-06-29
Cascade9- 1. Thanks for that info on Visiontek vis a vis ATI. Now I can stop hunting for a better solution to the card I now have.

2. I was 95% sure that adding more RAM was no solution. But I thought someone who understood the Linux architecture better than I do would contradict this. You have confirmed it.

3. This is the part I don't get- multithreading. I did not say that I had one core running and the other one idle. Both cores are splitting the load, and I thought this was the definition of multithreading.But they are each taking on their half of the load at half of their potential. The prime number list that I wrote and ran on windoze was done on some freebee Basic compiler (Tiny Basic), yet windoze ran it at 100% on each core. I cannot find a program or application anywhere that uses anywhere near 100% of both cores in Ubuntu, which leads me to believe that there is a bottleneck somewhere that could and should be eliminated. What is the sense of buying a high performance processor when it looks like Ubuntu (or the kernel) will only use half of its power?

---

