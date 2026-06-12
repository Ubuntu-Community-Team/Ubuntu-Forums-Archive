---
title: "removing grub/ubuntu"
date: 2010-11-24
forum: General Help
---

### Post by selittl on 2010-11-24
I am currently dual booting win 7 and maverick meerkat using grub.  I would like to revert to only a win 7 machine and boot directly into that.  Is it possible to remove grub and ubuntu and boot only into win 7?  How does one do this?

---

### Post by sikander3786 on 2010-11-24
Yes you can do that easily by just deleting the Ubuntu partition and then using the Windows 7 disc to repair startup and get rid of Grub.

If you are unsure, from Ubutnu, please post the output of

```
sudo fdisk -l
```

---

### Post by selittl on 2010-11-24
Thanks, however this is what happened:  Deleted ubuntu partitions, rebooted using win 7 disk, tried to repair startup and it tells me that no problems were found and now will not boot at all.  only boots to 
"error: unknown filesystem.
grub rescue>"

so guess that was a mistake, eh?

---

### Post by oldfred on 2010-11-24
Your repair must not have worked. Is windows in a primary partition. Do you have the boot flag (active partition) on the boot partition which may not be your main install.

Even with windows command line repairs work better.:)

At the minimum you need:
BootRec.exe /fixmbr

oldfred's Windows Vista/Win7 repair links:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

---

### Post by drs305 on 2010-11-24
If you have an Ubuntu LiveCD you can easily solve your problem, at least temporarily.

Boot the LiveCD and open a terminal. Install *lilo*, and run the second command. During these commands you will get messages about lilo not being completely installed. That is ok.


This assumes Windows is on sda (first drive).
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
If you want to get back the real Windows bootloader you will have to do so via Windows disk, repair disk or equivalent.

---

### Post by coffeecat on 2010-11-24
You need to repair the Windows MBR. Reboot with the Win7 disc, go into the recovery/repair option and then open a command window. Run Bootrec /FixMbr. See:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

**Edit:** oldfred beat me to it. :)

---

### Post by selittl on 2010-11-24
That seemed to do it.  Fixed!  Thanks!

---

