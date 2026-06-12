---
title: "Did I kill my Ubuntu partition?"
date: 2009-10-06
forum: General Help
---

### Post by Cringer on 2009-10-06
Below is a picture of what I am getting trying to boot into Ubuntu 9.04. I also booted up with a live CD and can not access anything. I tried to check sda4 (my ubuntu partition) with Partition Manager and it gave me an error. I saved the details onto my flash drive but now can't find it so who knows if it actually saved, I know in mentioned an I/O error which is also mentioned below.  When I tried to exit the Live CD I also got the below screens. I have several pictures as what happened below took a while to cycle through and that is just the end. Most of it looks like the pic to me.

If anyone knows what the heck happened from below please let me know.

**extra details that may or may not have to do with this. I was in Ubuntu with my Palm Pre hooked up via USB. I was editing pictures on the Pre, simple resizing. I started getting errors while resizing and my thumbnails were not loading of the pictures I was editing. Laptop started to bog down more, I tried to open System Manager and it wouldn't open with several attempts. I started closing stuff, nothing helped. I rebooted and this all started.

Thanks in advance. I am expecting to hear I just lost everything but I will hold onto the slim hope I can save things.

HP laptop
4 partitions; sda1 Vista (currently on this now), sda2 10 GB not used, sda3 is 2GB swap patition, sda 4 is Ubuntu 9.04

[IMG]

---

### Post by pastalavista on 2009-10-06
What I would do is boot the live CD to the desktop and click the install icon and select the MANUAL installation. At the partition editor, UNCHECK all the 'format' boxes for all the partitions including '/'. Then procede with the installation using the exact same username. It won't erase anything but just replace the original Ubuntu system files. You may have to reconfigure a few things afterwards though.

---

### Post by scragar on 2009-10-06
I think this is a problem with the file system for some reason, there are tools to fix it on any liveCD.

[http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html](http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html)

---

### Post by Cringer on 2009-10-06
Thanks guys. I tried suggestion #2 first and it didn't work. I thought it might but nope. So #1 it was, and it worked well enough. The only thing that appears lost so far that really hurts is Thunderbird being gone, so my email history will have to download over night.

Now for trying to get drivers installed. For some reason it is not giving me the option to install my wireless and nVidia drivers. I am off to figure out that one now.

---

### Post by fluffman86 on 2009-10-06
are you connected to the internet with an ethernet cable?  Sometimes you have to be online for you to get the recommendations for drivers.

---

### Post by Cringer on 2009-10-07
It took an internet connection plus downloading every software and security update that was needed because of the fresh install. Well, not all of them were needed, but I hit all just because it was going to be needed. After that and the required restart I was able to get my drivers.

Now it's on to finding out all the little things I am missing, like flash which I am installing now.

---

### Post by QIII on 2009-10-07
When you get Flash installed, be sure to remove swfdec and gnash.  They conflict with Flash.

---

