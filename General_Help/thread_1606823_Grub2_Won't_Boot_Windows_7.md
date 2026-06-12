---
title: "Grub2 Won't Boot Windows 7"
date: 2010-10-27
forum: General Help
---

### Post by cipher202 on 2010-10-27
Hi,  I upgraded a while back to Windows 7.  I run two separate HDDs, with debian on sda and windows on sdb.  Everything worked fine, up until i upgraded to windows 7.  The installer forced me to unplug sda and make sdb primary.  After installing I repositioned the HDDs and was stuck with a "NTLDR is Missing" message.  After removing the search -fs--uuid tag from grub.cfg, Windows 7 booted for a good 0.5 sec and then rebooted.  All that flashed was the "Starting Windows" page.  I see similar bugs reported in the launchpad, but nothing that directly parallels this.  

Any suggestions?  Here's my windows entry in grub.cfg:

```
menuentry "Microsoft Windows 7 Ultimate (on /dev/sdb1)" {
        insmod ntfs
        set root=(hd1,1)
        drivemap -s (hd0) ${root}
        chainloader +1
}

```Changing ${root} to (hd1) makes no difference.  Also, I've been using Windows 7 for moths now without a problem, it's only when I try and boot it form grub2 that I get a problem.  Physically removing sda lets Windows 7 boot fine.

---

### Post by dcstar on 2010-10-27
> **cipher202 said:**
> Hi,  I upgraded a while back to Windows 7.  I run two separate HDDs, with debian on sda and windows on sdb.  Everything worked fine, up until i upgraded to windows 7.  **The installer forced me to unplug sda** and make sdb primary.  After installing I repositioned the HDDs and was stuck with a "NTLDR is Missing" message.  After removing the search -fs--uuid tag from grub.cfg, Windows 7 booted for a good 0.5 sec and then rebooted.  **All that flashed was the "Starting Windows" page**.  I see similar bugs reported in the launchpad, but nothing that directly parallels this.  
.........

Grub is obviously booting Windows, it is Windows that has the problem, probably because it was installed **without** the other hard drive.

If Windows configured itself to believe it was on the first hard drive and now it finds itself on the second drive, then Windows needs to be reinstalled to match the configuration you are trying to run it in.

This is not an Ubuntu problem, it is a Windows problem.

---

### Post by garvinrick4 on 2010-10-27
If you have Ubuntu on one HDD and Windows on another HDD sda and sdb if while in Ubuntu if you run 
```
sudo update-grub
```while in Ubuntu it will use a prober to find windows and put it in grub menu.
or
```
sudo grub-mkconfig
```will make a new config file also
and should boot them both. But if you start Windows drive first in order
will always only boot Windows has no where to look for grub2.

IF it is Windows you are having trouble with as stated:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

If you want to post the whole boot file run this and post takes 30 seconds.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

---

### Post by oldfred on 2010-10-27
If possible I would physically switch drives. If SATA switch ports, so windows is sda & Debian is sdb. Linux will not care but windows really likes to be sda. You may have to check boot in BIOS and run an update for grub after.

The missing ntldr is a XP error. Did you have XP on this system at one time? Win7 does not use ntldr.

---

### Post by cipher202 on 2010-10-27
Thanks for the responses.

I actually found out (from another bug report) that Windows 7 doesn't like the drivemap call on grub2.  Removing the drivemap -s (hd0) ${root} let Windows boot fine.  Now that I think about it, I remember not understanding why it was necessary to set root, do the search for the partition by fs--uuid, and then switch the drive orders again.  Now I have it simply setting the root and chainloading.  Makes a lot more sense.

```
menuentry "Microsoft Windows 7 Ultimate (on /dev/sdb1)" {
        insmod ntfs
        set root=(hd1,1)
        chainloader +1
}

```I hope this helps anybody stumbling across this.

---

### Post by cipher202 on 2010-10-27
> **oldfred said:**
> The missing ntldr is a XP error. Did you have XP on this system at one time? Win7 does not use ntldr.

This is very interesting.  My guess is the new bootloader hasn't updated it's error screen.  I think setting the fs--uuid left the partition selected as the boot partition, when the bootloader was on the master boot record or first few sectors of the drive, hence the error.

---

### Post by cipher202 on 2010-10-27
> **garvinrick4 said:**
> If you have Ubuntu on one HDD and Windows on another HDD sda and sdb if while in Ubuntu if you run 
```
sudo update-grub
```while in Ubuntu it will use a prober to find windows and put it in grub menu.
or
```
sudo grub-mkconfig
```will make a new config file also
and should boot them both. But if you start Windows drive first in order
will always only boot Windows has no where to look for grub2.



I would have tried that before posting, but the os_prober was what gave me the menu entry that I was using to boot XP.  Perhaps it would have generated a different one for Windows 7, though.

---

