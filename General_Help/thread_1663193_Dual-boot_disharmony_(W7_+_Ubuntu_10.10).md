---
title: "Dual-boot disharmony (W7 + Ubuntu 10.10)"
date: 2011-01-09
forum: General Help
---

### Post by goreyduke on 2011-01-09
I've tried following "How to dual-boot Windows 7 and Ubuntu in perfect harmony" but have ended up unable to boot anything. 

On booting, I get the message "error: no such partition. grub rescue>-" Can someone help, please?

This is after hours and hours of trying to follow the above advice to partition my 120GB drive into a 25GB NTFS partition for W7, a 15GB unformatted for Ubuntu 10.10 and the rest for storage.

The problems began when using W7's Shrink Volume, which did not want to relinquish anything less than about 58GB (i.e. half the disc). 

An Auslogics Disk Defrag scan showed one "allocated space" file in the middle of the disc, which would not move. GParted, used from an Ubuntu 10.10 live CD, seemingly solved this (easily) but the booting has not been the same since.

I installed Ubuntu 10.10 on a separate, adjacent partition and now think I blundered when I made this partition bootable.

W7 disappeared on boot-up. Then it came back again, and now it's gone again. I'm convinced W7 is still there as GParted and Disk Utility show the disc space still being taken up.

I have deleted the Ubuntu 10.10 partition and installation and restored the NTFS partition to the whole disc (and made it bootable) but still cannot find the disc on boot up.

Is this something Ubuntu 10.10 can undo or is it a W7 issue? (and, if this gets sorted, is there an easier way to dual-boot?). 

Thanks

PS - am using a live CD to post this.

---

### Post by Quackers on 2011-01-09
Did you move the boot flag at all? If so, where is it now?
It may help if you boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by efflandt on 2011-01-09
Is Win7 able to boot now?  If not, you may need to run its recovery DVD several times to restore the Windows mbr and boot (unless you totally wiped its partition by formatting it).  But if Linux cannot see the NTFS partition, you may have changed it to an MS logical volume instead of regular partition(s) and Linux may not trust itself to deal with that.

What type of computer or drive is it that you are running Win7 on a 120 GB drive, or is it SSD?  If it is an older computer (especially with Asus mobo) it might not be able to cope with partitions aligned to MB boundaries, which is the default since 10.04 unless you use **partman/alignment=cylinder** kernel boot parameter during install (or check the box in gparted to "align to cylinders" if creating partitions before install).  I had that issue with an HP desktop from 2004.

Some Windows programs store data in what they think is an unused part of the mbr, which can step on grub.  So if everything works fine until you boot Win7 and then will not boot, you may need to either uninstall the offending Windows program or put grub somewhere else (like force it to a primary Linux partition, instead of mbr, and with Windows mbr restored, mark the partition with grub as boot partition with gparted).  I had that problem with my new Dell.

---

### Post by goreyduke on 2011-01-09
No luck, I'm afraid.
There was no "Try Ubuntu" option on the live CD, so I reinstalled Ubuntu 10.10 in the hope this would allow me to download the boot script info to the desktop.

But on reboot, I had the same error-grub-rescue message. 

I can tell you that the old Ubuntu partition (before the recent reinstall) had a flag in boot. Then I deleted the partition and made the NTFS partition bootable (with a flag).

Disk Utility and GParted now say I have a 63GB bootable ntfs partition (with a flag) and an extended 55GB partition made up of a 53GB linux partition and a 2GB swap.

I'm lost.

---

### Post by Quackers on 2011-01-09
In Win 7 it is likely that the boot flag should be on sda1 (a small partition with boot files in it - maybe only 100MB ).
You may also need to restore the mbr with the Win 7 repair disc, by running startup repair 3 times.

---

### Post by goreyduke on 2011-01-09
Thanks both. I will try the recovery disc and see how it goes.

It is a fairly old machine (4-5 years) but shouldn't be that out of touch. It dual-booted with no problem before (XP and Intrepid, etc), but this time I wanted to access all my folders from both OSs.

---

