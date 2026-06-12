---
title: "Noob Ubuntu issues :)"
date: 2010-10-22
forum: General Help
---

### Post by Daniel06GT on 2010-10-22
Hey guys, I just installed Ubuntu 10.10 and I'm super excited about it, love the freedom, speed, and customization you can have with it, but i'm havin just a couple of minor glitches that I'd like some help with please.

I know you can manually have it save the state of running apps so when the next time you boot up the PC it starts all the programs etc you had running, when I do that it doesn't work. :P

Second I have 3 hard drives on my PC on SSD running Windows, a second SSD running Ubuntu and a 3rd with all my Data. WHen I boot up Ubuntu it doesn't pick up my 3rd HDD right away so it doesn't load my wallpapers or settings that call any info from that Drive. As soon as I hit My Computer it sees the HDD and it can call the info from it, but i have to go back to Appearance and choose the Wallpaper.
To confirm this was the problem, I moved the Wallpaper pic to my local Pictures folder and when I restarted the wallpaper was there, but my Saved state settings were still "out of whack".

Any help would be appreciated. 
Thanks a bunch.

---

### Post by nearlymagicman on 2010-10-22
> As soon as I hit My Computer it sees the HDD and it can call the info from it I ain't so experienced with Ubuntu myself but if you literally have to hit your computer, my guess would be more of a hardware than a software problem.

---

### Post by Daniel06GT on 2010-10-22
> **nearlymagicman said:**
> I ain't so experienced with Ubuntu myself but if you literally have to hit your computer, my guess would be more of a hardware than a software problem.

hahaha wrong choice of wording. Click "My Computer".

---

### Post by AoSteve on 2010-10-22
LMAO!   Use the FM to get to the picture in the folder.   Open it and set as desktop wallpaper.   I believe it's in the tools manager.  

FM = File Manager aka "My Computer"  LOL

---

### Post by frukukuk3 on 2010-10-22
am new to ubuntu too have u seen compiz fusion ? if uv not check youtube for vids thats what made me change OS 
guide to install -http://ubuntuforums.org/showthread.php?p=9978292

:guitar:

---

### Post by Hack.The.Pow. on 2010-10-22
Sounds like your computer is just not mounting your data drive on startup.  How is the drive formatted?  If it is NTFS download something from the Software center called NTFS Configuration Tool.  This will let you mount the drive on startup pretty easily with a gui.

Also what do you mean by the running apps don't restart after a shutdown?  How are you trying to go about doing this?

---

### Post by bcbc on 2010-10-22
hibernation requires a swap partition with a size greater than the size of your ram. The required size is nebulous but I've seen it described as RAM + overflow. And since Maverick seems to use a lot of memory, you probably need a large swap. (There are some other tweaky bits you need to do when you create a swap partition to get it to hibernate - this is not made easy in Ubuntu). 

You need to mount your data partition in /etc/fstab - when you click on it under Places, it's actually mounted for the first time - and you can't access anything unless it's mounted. So puttting it in fstab will mount it at the same time as your / (root) is mounted.

Set up hibernate:
1. first set up swap partition
2. figure out uuid (sudo blkid)
3. add swap to /etc/fstab (UUID=xxxx none swap sw 0 0 )
4. add swap uuid to /etc/initramfs-tools/conf.d/resume  (RESUME=UUID=xxxx)
5. update initramfs (sudo update-initramfs -u)

---

### Post by Daniel06GT on 2010-10-22
> **Hack.The.Pow. said:**
> Sounds like your computer is just not mounting your data drive on startup.  How is the drive formatted?  If it is NTFS download something from the Software center called NTFS Configuration Tool.  This will let you mount the drive on startup pretty easily with a gui.

Also what do you mean by the running apps don't restart after a shutdown?  How are you trying to go about doing this?

Thanks when I get home i'll download that app and hope it works!! :) and yes I do have NTFS. 

System>Preferencs>Startup Applications you can manually save the desktop state right?? 
I might be wrong but isn't the purpose of this so that everytime you boot up your PC it loads what you had running at that moment?

---

### Post by Hack.The.Pow. on 2010-10-22
> **Daniel06GT said:**
> Thanks when I get home i'll download that app and hope it works!! :) and yes I do have NTFS. 

System>Preferencs>Startup Applications you can manually save the desktop state right?? 
I might be wrong but isn't the purpose of this so that everytime you boot up your PC it loads what you had running at that moment?

Ahh now I know what your talking about.  On an old Ubuntu install I remember it had a feature that accomplished this quite nicely.  I tried what you just mentioned and that didn't work for me either.  Theres probably something were just missing.

Have you tried getting hibernation to work yet?  It accomplishes the exact same thing.

---

