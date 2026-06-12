---
title: "grub rescue&gt; I got when booting up???"
date: 2010-05-07
forum: General Help
---

### Post by toddnfam on 2010-05-07
Ok, first I know nothing when it comes to ubuntu and code.  I went to upgrade from a dual boot Windows XP/Ubuntu 9.10 to Windows XP/Ubuntu 10.04 and it seemed to work flawlessly.  However, when I exited to reboot into xp, it was like I was stuck in a boot/loop that kept bringing me to the boot menu.  I went back into 10.04 to search the internet for help and found a link that told me to sudo fdisk -l, said to mkdir media/dev/sda5 or something like that, and then I rebooted and got grub rescue prompt.  This is what i get now off my 9.10 ubuntu live, is there a semi-simple fix without losing my upgrade and dual boot?
 ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15752021

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13287   106727796    7  HPFS/NTFS
/dev/sda2           13288       14593    10490445    5  Extended
/dev/sda5           13288       14531     9992398+  83  Linux
/dev/sda6           14532       14593      497983+  82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       34986   281025013+   7  HPFS/NTFS
/dev/sdb2           34987       38913    31543627+   f  W95 Ext'd (LBA)
/dev/sdb5           34987       38913    31543596    b  W95 FAT32
u

---

### Post by toddnfam on 2010-05-07
Ok, I ran instructions below from link on message board and I'm back to where I was when I initially upgraded.  I'm stuck in a loop when I try to boot Windows XP at menu, 10.04 works like a charm though...any ideas so I can boot into XP?

From that you need to find the device name of your Ubuntu drive,  something like “/dev/sda5&#8243;.
 So, still in the terminal, type:
 	Code:
 	sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5 
And then, to reinstall the grub:  	Code:
 	sudo grub-install --root-directory=/media/sda5 /dev/sda

---

### Post by oldfred on 2010-05-07
ARe you still able to boot Ubuntu? Did you try to reinstall grub2 but actually have grub legacy.

Was the original problem booting windows?

So we can see what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

