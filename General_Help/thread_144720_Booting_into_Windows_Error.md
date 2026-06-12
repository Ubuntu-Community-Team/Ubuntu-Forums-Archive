---
title: "Booting into Windows Error"
date: 2006-03-14
forum: General Help
---

### Post by wikiwooo on 2006-03-14
I hope this is in the right section.

I recently aquired a 250 gigabyte SATA HDD.  Happy, that I finally had two physical drives, I immediately installed windows on the new HDD and installed ubuntu on the old one (120 gigabyte ATA133).  Everything was working fine.  Then I tried to boot into windows after installing Ubuntu.  In the grub menu, windows was not an option.  Confused, I booted into Linux and came here to help solve my problem.  After some searching I found some things about editing the menu.lst file.  I had a friend (who is very proficient with linux) come over and make a new option in the menu to boot windows.  When I selected this in the grub menu, all it would do is have an error.  Now I tried many different things and eventually (after some changing of the boot order in the bios), my friend told me that my windows install had somehow gone bad since I installed ubuntu.  No problem.  I simply unplugged the linux drive (so as not to screw it up) and installed windows again on the 250 gig.  This worked fine.  Now, I plugged the linux drive back in, booted to it, put the right commands in the menu.lst file, and restarted to try again.  This time when I tried to boot windows, I got an "NTDLR Missing" error.  I read that this means something about your OS installation is messed up.  Well, when I changed the bios to boot from my windows HDD first, I got the same error.  However, If I unplug the linux HDD, windows boots fine.  In fact, I am in windows (XP Home Edition) right now, so nothing is wrong with my OS.  I was wondering if anyone could explain this to me.  
I will boot into linux in a minute and post exactly what is entered in my menu.lst for windows.

Sorry for this being so long.

Ok, in linux now.  Here is what my menu.lst has.

title        	Windows XP Home Edition
map		(hd2) (hd0)
rootnoverify	(hd2,0)
chainloader    +1

Is there anything wrong with that?  Just to verify, I have tried having two map commands, but read that the second was not needed.

---

### Post by dcstar on 2006-03-15
[QUOTE=wikiwooo]
.......
Ok, in linux now.  Here is what my menu.lst has.

title        	Windows XP Home Edition
map		(hd2) (hd0)
rootnoverify	(hd2,0)
chainloader    +1

Is there anything wrong with that?  Just to verify, I have tried having two map commands, but read that the second was not needed.[/QUOTE]
As far as I can see, you are telling Grub that you want to map your third detected drive (hd2) to your first drive (hd0), and then boot off the first partition.

Do you have three drives?

---

### Post by wikiwooo on 2006-03-15
Yes, I have a 250 gig sata with windows, I have a 120 gig ata with linux, and a 40 gig ntfs for backup of my windows files.

---

### Post by gkiller on 2006-03-15
I had Windows installed on my SATA drive, and then installed Linux also on that drive. I have 2 other IDE drives in my system, and I also could not boot to Windows.

My problem was solved when I unplugged the IDE drives and reinstalled Ubuntu. After that I could plug in the IDE drives and everything worked.

But since you are installing Linux on the IDE drive unplugging is not an option for you.

But when installed with IDE plugged in, the menu.lst entry for windows had also map commands and root (hd2,0).

After installind with IDE unplugged, the map commands were gone and root (hd2,0) was replaced with root (hd0,0)

And this worked.

So apparently Ubuntu Installer detected the SATA drive as the 3rd drive, but it is really the 1st drive. Maybe you can solve your problem by removing the map command and putting rootnoverify (hd0,0).

I'm not sure if this is important, but in the BIOS boot order options the SATA drive (listed as SCSI) is set before the IDE drives. I don't know if this affects the hd numbering of GRUB or not.

Remember to reinstall the GRUB to the MBR after doing the changes to menu.lst with
```
sudo grub-install /dev/hda1
# insert your linux partition instead of hda1
```

---

### Post by wikiwooo on 2006-03-15
I can't try that at this instant (working on something else) but I will try it first thing tomorow and let you know how it goes.  Thanks very much.

---

### Post by wikiwooo on 2006-03-16
I tried it and i got Error 13: Invalid or Unsupported executable format.

Here is the entries in my "device.map" file:

> (hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/sda1


That is where I originally got the idea that my sda (serial drive) was hd2.

Are there any other ideas out there?

Thanks very much!

---

### Post by gkiller on 2006-03-16
Hm.. yes of course, if you just change the menu.lst but not the device.map it won't work.

Try the following in your device.map
```
(hd0) /dev/sda1
(hd1) /dev/hdb
(hd2) /dev/hda
```
and run grub-install again.

Although I'm not sure why the entry is 'sda1' instead of 'sda'.

In my device.map I have a single entry:
(hd0) /dev/sda
But that's of course because I don't need the IDE drives for booting. After my first install I had the same device.map content as you (except for sda instead of sda1), which didn't work for me.

Depending on your menu.lst maybe you also have to exchange hd1 and hd2 so that GRUB finds your Linux partition.

You might want to backup your menu.lst and device.map with
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
# and same for device.map
```
And if you suddenly can't boot into Linux anymore, you can boot from the Ubuntu install CD, and enter 'rescue' at the boot: prompt. Then you can mount your linux partition and copy the original menu.lst and device.map back, and grub-install again, to revert to the original state so that you can at least boot again.

---

### Post by wikiwooo on 2006-03-16
I tried and I get error 13 again, when booting both linux and windows.

---

### Post by gkiller on 2006-03-16
OK, then I cannot help you unfortunately anymore, since I don't know enough about GRUB besides what I already told.

I hope you can solve your problem somehow :)

If all else fails, you could consider installing both Windows and Linux on the SATA drive, on different partitions. That should be the exact same situation that I had, and maybe unplugging your IDE drives for the installation would work for you as well.

---

### Post by wikiwooo on 2006-03-16
Thanks for the suggestion.  I may do that, if this goes unsolved for very much longer.

---

### Post by wikiwooo on 2006-03-18
Bump

Any other suggestions?

---

### Post by wikiwooo on 2006-03-19
Last bump, things move down fast in this section.

---

