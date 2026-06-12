---
title: "I'm basically begging for someone to help me out."
date: 2011-11-21
forum: General Help
---

### Post by ubchris on 2011-11-21
Okay, 
So I want to say I've been at this for a month, trying to rescue my laptop from the clutches of GRUB. 

Here's the problem: 
I'm a n00b Ubuntu user that looks up error codes on google and fixes them accordingly. 

I don't know anything* about Ubuntu, but I got my way around pretty well by reading forums like this one, and I'm really hoping someone can guide me in the right direction. 

Here's what I did. 

-Installed 11.04 on a dual-boot with Windows. 
-Weaned myself off of Windows and decided to boot solely with Ubuntu. 
-Figured I'd never need Windows again (sound like a familiar story?) and reinstalled Ubuntu 11.04, writing GRUB to my MBR. 
-My summer break shortly expired and I needed to get back on campus, which meant using programs unsupported by Natty. 
-A stupid thought occurred: "Well, whatever. I don't want to go through the trouble of completely uninstalling Linux, so I'm going to reformat my whole hard drive via my Windows 7 retail disk." 
-Thinking it worked, and booting into Windows, everything is great. Literally, everything worked. My computer crashed, maybe two or three times, and then I get this message: 
```
Try (hd0,0): NTFS5: No grldr
Try (hd0,1): invalid or null
Try (hd0,2): invalid or null
Try (hd0,3): invalid or null
Try (hd1,0): NTFS5: No grldr
Try (hd1,1): invalid or null
Try (hd1,2): invalid or null
Try (hd1,3): invalid or null
Cannot find GRLDR. 
Press space bar to hold the screen, any other key to boot previous MBR...
```

I've run all sorts of commands on the command prompt on Windows. I'm literally at my wits' end, googled endlessly across weeks and weeks of this problem remaining unsolved, with over 13 Ubuntu reinstallations, and countless Windows reinstallations. 

So, I'm pretty much begging anyone that can help to please do so. 
I'll stay online for the next couple hours to respond to your replies. 

Thanks,
Chris

---

### Post by alphaamanitin on 2011-11-21
Sounds like some corruption.  Boot live image of Ubuntu and check your hard drive health.  Personally, I would zero the drive out with the dd command and reinstall windows after that.  

AlphaA

---

### Post by ubchris on 2011-11-21
> **alphaamanitin said:**
> Sounds like some corruption.  Boot live image of Ubuntu and check your hard drive health.  Personally, I would zero the drive out with the dd command and reinstall windows after that.  

AlphaA

How would I go about doing that? 
I can boot into Ubuntu through the live disk, but then what?
My ultimate goal is to just run Windows stable for now.

---

### Post by collisionystm on 2011-11-21
It sounds to me that the MBR was never wiped completely clean.
GRLDR is a part of grub from the wubi install if i am not mistaken. Grub itself is unaffected by it, but obviously the windows mbr is.
You need to fix your mbr.

Go here
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

and get resca tux.

grub is a virus to windows machines. I always remove all usb drives and others when installing. Grub stamps its mark on everything. Little B######

---

### Post by jimmydean886-2 on 2011-11-21
To do that you would just insert the Live CD, then when you see the purple screen with the accessibility icon and the keyboard icon, hit the down or up arrow key. You will then see a bunch of languages. Select yours, then choose "scan hard disk for failiures" (this may not be worded quite the same) and just follow the prompts. If there isn't any such option, boot from the live CD and open up the "Disk Utility". Don't make any changes, just open up the selection for your hard disk. It should give you a health status.

Another solution: try a dual boot. GRUB is (suprisingly) a much more stable boot loader than windows bl. I've never personally been able to bypass the windows one on my laptop, but it doesn't even access the windows XP one on our desktop.

Try testing the disk first though.

Hope it helps! :)

---

### Post by Mark Phelps on 2011-11-21
Sounds like what you want to do is reinstall Windows 7.

The BEST source of Win7 technical advice is the Windows 7 forums: sevenforums.com.

From their site, the link below tells you how to restore the Win7 MBR from your disk:

[=Installation and Setup"]http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html?filter[3]=Installation and Setup]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html?filter[3)

There are additional tutorials in that section that tell you how to restore Win7 boot using Startup Repair.

You need to read their tutorials and follow their suggestions.

---

### Post by ubchris on 2011-11-21
As far as reinstalling Windows: I've already done that, multiple times to no avail. It'll work for the first couple of boots, but suddenly, it'll give me the message if my computer overheats and shuts down on it's own. 

As far as my hard drive being healthy: Ubuntu says that it's healthy. 

Also, I've tried doing [all] of the bootrec commands on Windows to completely nuke the bootloader and rebuild it myself, and nothing happens. It'll work for the first couple times like I've said before, and then it just goes back to the usual.

---

### Post by oldfred on 2011-11-21
If you have a full retail Windows 7, you do not have grldr. 

It was my understanding that some illegal installs used grldr as a workaround for Windows licensing. The grldr is just grub4dos that is used by wubo and some other applications that are not Windows but run from NTFS or DOS.

[http://grub4dos.sourceforge.net/wiki/index.php/Main_Page](http://grub4dos.sourceforge.net/wiki/index.php/Main_Page)

---

