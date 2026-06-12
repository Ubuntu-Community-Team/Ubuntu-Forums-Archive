---
title: "Trying to uninstall ubuntu for Windows 7?"
date: 2010-10-17
forum: General Help
---

### Post by Super Planet Man on 2010-10-17
It seems like all I can find as far as tutorials are for dual booting... I simply want to delete my ubuntu operating system and replace it with Windows 7. There is no data that I need to save, I just need to delete it. I'm actually not too great with computers, and you guys are my only hope! Thank you so much!

---

### Post by ivarn on 2010-10-17
Login to windows, go to disk manager and delete the linux partition. 
The windows partition is called NTFS, now pop in the win7 cd, restart the pc and boot it up.
Now click repair. This will fix your MBR and delete ubuntu from the list.

---

### Post by Super Planet Man on 2010-10-17
I can't log into windows, it's not installed on this computer. I have Ubuntu installed but want to delete it for a full windows system.

---

### Post by Ms_Angel_D on 2010-10-17
Hi super.

Before doing the following make sure you have backed up all your important files.

Then all you need to do is boot to the live cd and use gparted

insert your ubuntu disk and upon boot select the option to try ubuntu.

once the desktop is loaded select

system->administration->gparted

Right click on your swap partition and set it to "swap off" then delete it along with any remaining partitions. then format the drive to NTFS. Once thats done shut down and switch to your windows 7 disk, upon reboot the windows 7 disk should load and proceed to give you all your install options.

---

### Post by Super Planet Man on 2010-10-17
Okay I did the following:

Opened GParted and deleted partitions under /dev/sda2. I can't delete /dev/sda1. I also can't figure out how to format the hard drive to NTFS... I feel like such a linux noob. ):

---

### Post by ivarn on 2010-10-17
Do part one of what I said after you have installed windows.
Just open up Disk Manager in windows 7 and delete the partition from there.
The Windows installation will wipe out grub so you don't need to do the 2nd part.

---

### Post by Halfbrazilian on 2010-10-17
All you need to do is load the Windows 7 disk, delete all the partitions with the installer tool during the installation, and create a new NTFS partition to install on. I wouldn't be surprised if the Windows 7 installer gives a option to just install on entire drive.

---

### Post by Super Planet Man on 2010-10-17
It doesn't seem to be reading my Windows 7 disk. When I go to boot menu and CD drive, it simply just boots ubuntu again, despite the Windows 7 disk in the drive.

---

### Post by GreatKeyHunter on 2010-10-17
> **Super Planet Man said:**
> It doesn't seem to be reading my Windows 7 disk. When I go to boot menu and CD drive, it simply just boots ubuntu again, despite the Windows 7 disk in the drive.
Is that win 7 a cd or a dvd cd?

---

### Post by Super Planet Man on 2010-10-17
DVD CD, sorry for being vague.

---

### Post by GreatKeyHunter on 2010-10-17
> **Super Planet Man said:**
> DVD CD, sorry for being vague.

Can your drive play dvd's?  If not that might be the reason why it is not reading it.  I had something like that happen to me in the past and i went crazy trying to figure out why it was not reading the cd inside.

---

### Post by Super Planet Man on 2010-10-17
Yes, it can read DVDs. I'll try to reboot again.

---

### Post by Dans564 on 2010-10-17
Press escape when bios is loading and change the boot priority in boot settings to boot cd first. Put the DVD in and restart. When in the windows 7 DVD select advanced install instead of upgrade install. Next u will see a window with all ur partitions. Systematically delete each partition. Now once all are deleted u will click on the free space line and select format. Once this is done u can install win 7 normally.

---

### Post by wilee-nilee on 2010-10-17
Sometimes the per session post bios choose boot from menu is needed. You get there with a key prompt at startup mine is f12, but on various computers it can be esc or any other key really.

---

### Post by Super Planet Man on 2010-10-17
I changed the boot priority to the CD-ROM drive with the Windows 7 disk. It still loads ubuntu every time. I'm really not computer savvy at all, my apologies!

---

### Post by Dans564 on 2010-10-17
Hmmmmm..... When my windows 7 DVD is loading it says press any button to boot from cd or if time expires it will just go to grub. So try looking for that

---

### Post by Quackers on 2010-10-17
Do you have another computer to see if the Windows 7 cd works in that? 
Are you sure the disk is bootable? Have you used it before? Where did you get the disk from?

---

### Post by Dans564 on 2010-10-17
We won't judge if it's pirated lol

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
Also we won't judge you for uninstalling Ubuntu for a worse OS :)! Just kidding! It might sound silly but are you sure you're selecting to boot from a CD? Does it have an asterisk or something to indicate the current option? Also have you searched YouTube? There are many helpful videos and some of them are about uninstalling Ubuntu. And if none of those help you, you can install Ubuntu all over again (it doesn't take much time anyway) and try to do the steps the guys mentioned before. If you do that be sure to select to install Ubuntu and use the whole disk. Hope any of that helps!

---

