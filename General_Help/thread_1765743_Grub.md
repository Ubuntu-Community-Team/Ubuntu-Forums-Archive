---
title: "Grub"
date: 2011-05-23
forum: General Help
---

### Post by poliltimmy on 2011-05-23
I have 10.04 and 11.04 in dual boot. Could someone please explain how I can get back to exclusively 10.04. I am nervous about the GRUB change.

---

### Post by Quackers on 2011-05-23
Are both installs on the same drive?
Which drive is that (eg /dev/sda)?
Which entry is first in the grub menu?

---

### Post by ajgreeny on 2011-05-23
Do you mean you want to totally remove 11.04?

If you do I suggest you boot to 10.04 (from whichever grub is used at the moment, 11.04?) and then from the running 10.04 use command ```
sudo grub-install /dev/sda
``` This assumes you have a single disk, sda, and that you have not done anything to grub in that install, even though you are probably not using 10.04 grub at the moment.

This is something I have had to do sometimes when I forget to put grub from one of the OSs I have on a multibooting second drive onto sdb, instead of sda.  Providing it is possible to boot to the OS from which you want to run grub, it is the work of only that one command.  If you have more than one disk you need to give more details of your OSs, so the output from the command ```
sudo fdisk -l
``` would be useful.

---

### Post by poliltimmy on 2011-05-23
Thanks for the response.

Yes both same drive.
sda1 is my data partition
sda5 is 10..04

I tried to attach a GParted shot. Hope it works and helps.

---

### Post by poliltimmy on 2011-05-23
Yes I mean to remove 11.04. I hope this is what you asked for. GRUB 1.99 in use.

$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13341334

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25667   206162977   83  Linux
/dev/sda2           25667       38913   106404705+   5  Extended
/dev/sda5           28810       38290    76156132+  83  Linux
/dev/sda6           38291       38913     5004216   82  Linux swap / Solaris
/dev/sda7           25667       28549    23148544   83  Linux
/dev/sda8           28549       28809     2086912   82  Linux swap / Solaris

---

### Post by Quackers on 2011-05-23
Thanks.
If you follow ajgreeny's advice that will safeguard against any problems.
Once that's done you can then just delete or re-format the partition used by 11.04 then run sudo update-grub to clean up the grub menu.

---

### Post by poliltimmy on 2011-05-23
Done deal.
:popcorn:Thanks a bunch guys!!!!

---

### Post by Quackers on 2011-05-23
Nice one :-)
Tasty popcorn that :wink:

---

