---
title: "Ubuntu not booting.. help? :("
date: 2011-08-08
forum: General Help
---

### Post by noneabove1182 on 2011-08-08
Hey guys, so, here's my problem...

First info : i used the wubi.exe to install a partition on my windows 7 HP Pavilion dv6 laptop.

Yesterday I was trying to install my graphics card driver and was doing a bunch of stuff I found on the internet, then it seemed to work, but when i rebooted, I was no longer allowed to use Unity... so, wanting to fix this but having no idea how, I decided, since i had next to nothing on my ubuntu, i would just uninstall the partition using uninstall-wubi.exe, then use the wubi.exe to reinstall. This worked fine (so i thought) but now, whether i attempt to start ubuntu normally or with recovery mode, i just get a bunch of white text and then nothing happens, no matter how long i seem to leave it.. I will upload a picture from my phone of the screen, but if you need to know what it says to judge the problem I will see about writing it all out.. Also if there is ANY more information you need to know, please ask instead of going away, because i would really like ubuntu to be working again, even if it means i have to ignore my graphics driver with the new partition.

Thanks for any and all help you can provide!

---

### Post by Sotanaht on 2011-08-08
Instead of writing out the whole thing, could you just write out the parts you think are relevant?  It looks like it's giving a bunch of error messages, but I can't read it and can't really help.  If one of the error messages specifies what it's having a problem with (either it specifies the device that's having problems or gives an error number) copy that down.  Before anybody can help, we have to know what the problem is exactly.

On a side note, I think you'd be better off installing Ubuntu from a LiveCD or LiveUSB.  Wubi might be causing the problem.  You could boot in with a liveUSB, then open GParted (I'm not familiar with Unity, so open it however you open system programs in Unity, or if that doesn't work, open a terminal with ctrl-alt-t and then enter "sudo gparted" to open it) and reformat the partition you created with wubi to either ext3 or ext4 (if you don't know the difference between the two, I'd recommend ext4, but some people prefer ext3).  Make sure you are ABSOLUTELY CERTAIN that it is the correct partition, and not your Windows partition, unless you want to lose all of your data (I don't think you want that :P).  Then proceed to run Ubuntu installer from the desktop icon, and put it in that partition.  Everything from that point on is pretty straightforward, just make sure when it asks where to install Ubuntu that you select "custom" or "advanced" or whatever it's called, and put it on the partition that you just formatted.

If this works, it's probably easier than any fix for the problem on your current install.

---

### Post by Sotanaht on 2011-08-08
Actually, before you reformat anything, you should use the wubi uninstaller first.  I'm not sure if it's actually necessary, but you're better safe than sorry.

---

### Post by Mark Phelps on 2011-08-09
First of all, Wubi doesn't create a new partition on your drive; instead, it installs inside an existing NTFS partition.  It uses a single file that BEHAVES like a partition to Ubuntu.

Second, BEFORE you attempt to force a dual-boot install into a new separate partition, look at the partitions you have using Win7 Disk Management utility.  If you already have four (OEM's typically configure PCs this way now), then you can NOT create any new partitions.  You will have to decide which partition you want to remove.

Third, if you DO want to go ahead with repartitioning, then before you do that, use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will come in useful later, should you need to restore the Win7 Boot Loader.

---

