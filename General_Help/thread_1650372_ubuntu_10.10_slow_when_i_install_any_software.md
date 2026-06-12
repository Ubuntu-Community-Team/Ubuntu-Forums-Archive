---
title: "ubuntu 10.10 slow when i install any software"
date: 2010-12-21
forum: General Help
---

### Post by Ghorab on 2010-12-21
My Computer is Dell OptiPlex GX270
Processor 2.9 cache 1 MiB
Ram 512 MiB
Hard Disk 160 GiB
installed version : Ubuntu 10.10

in standby CPU status "CPU History" over than %30 to %60 <- this status from system monitor - Resources tab.

when i install any software from terminal or deb package or install updates CPU status be over than %90 and the machine go very slow and stops working.
and after installing is finish i can use the computer without problems ...!

also if i open music files when i browsing the internet my computer be slow.

note that I installed Windows XP also on my machine and there was no problems !!!

please help me to solve this problem

---

### Post by ajgreeny on 2010-12-21
System Monitor itself is a bit of a resource hog, so look at cpu% in ```
top
``` in terminal instead, and you will probably see it is a lot lower than those figures you speak of.

I have no idea what processor you have, and your listing does not really help there, but certainly I think you are short of ram; 512 is a bit low.  Also the system is always likely to run slowly when it is installing packages, particularly with a single core cpu, which I presume is what you have, as 512 MB ram would never be used in an OEM machine alongside a dual (or more) core cpu.

Gert more ram if you can, and you may see an obvious speeding up of the system.

---

### Post by pricetech on 2010-12-21
The GX270 was quite a good computer in its day.  We still have a few in service here in an area where I'm very hesitant to put new hardware.

Its day, however, is in the past.

More RAM will help.  You should be able to put 2 gigs in it, which will make a big difference, but it's still not going to be a speed demon.

---

### Post by Ghorab on 2010-12-22
i hear about that Ubuntu works fine with hardware better than Windows XP
i installed Windows XP on the same machine but i don't have any problems or slow in XP ...!
this picture from the command "top" from terminal
[ATTACH]179151[/ATTACH]
CPU usage now %30 to %60 because i open only two tabs in Firefox and System Monitor only :D
but if i open two tabs more in Firefox CPU usage will arrive to %85 to %99 and my computer was freeze :(
and i don't have enough money to upgrade this computer now.
thank you all and i wish you suggest any solutions to me

---

### Post by ajgreeny on 2010-12-23
In that case I suspect some problem in your firefox profile.  backup the current hidden **~/.mozilla/firefox** folder in your home by renaming it **~/.mozilla/firefoxbak**, and then restart firefox.  If you can't see hidden folders in nautilus hit Ctrl+H and they will all appear.

If that solves the cpu usage problem then we know where it stems from, and can start pulling back all your bookmarks etc etc to the new profile.

However, one step at a time.  See if that works first, then come back again if needed and we can help you get a lot of data from your old profile back to the new one, but not all of it, or you will have the same problem, of course.

---

### Post by Ghorab on 2010-12-24
@ajgreeny
thank you for your interest, i follow your steps you told me. but nothing has changed :(
now i record video from my desktop, you will see my CPU usage between %90 to %100
i will upload the video very soon, you can see now in this photo CPU usage %99.1
[ATTACH]179286[/ATTACH]
please try to find solution for this problem, because I'm a boor youth and i can't upgrade my computer now or in near coming days

---

### Post by Ghorab on 2010-12-24
this is the video
[http://www.megavideo.com/?v=TO702JTL](http://www.megavideo.com/?v=TO702JTL)
please i have a question, if i remove ubuntu and install lubuntu i will be able to setup and apply ubuntu applications and updates on it ?
i mean that lubuntu have the same support from canonical? and i will got updates?

---

