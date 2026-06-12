---
title: "Grub error?!"
date: 2010-08-09
forum: General Help
---

### Post by geekman314 on 2010-08-09
Okay. I originally had windows vista on my laptop. I decided to try ubuntu and originally tried installing from windows. I later deicided i wanted to install it from a my usb drive. after i started ubuntu i put most of the programs i use most on it, and then i decided to reboot so i could go onto windows. anyway, It rebooted fine, and i saw the list of os's and picked "windows bootloader" after that, it started loading windows, then the screen turned gray and loaded up Acer's E-Recovery. I was confused by thbis and i clicked the exit button. After that, nothing was happening so i shut down my laptop. When i turned it on, it said "Error: No Partition" and then below that "grub> _". I have no idea what to do. I am using the "Try it!" part of my usb installer for ubuntu right now, so i can do minimal stuff to my laptop. Any help? All the forums i have looked at were really confusing, but it looks like you might need this to help solve my problem. It is "sudo fdisk -l" on the terminal:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x07e26584

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10490413+  27  Unknown
/dev/sda2   *        1307       10382    72900608    7  HPFS/NTFS
/dev/sda3           10382       10774     3145796    7  HPFS/NTFS
/dev/sda4           10774       19458    69750785    f  W95 Ext'd (LBA)
/dev/sda5           14996       19458    35838976    7  HPFS/NTFS

Disk /dev/sdb: 8040 MB, 8040480256 bytes
255 heads, 63 sectors/track, 977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bacf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         976     7839698    b  W95 FAT32

```

But i dont know. 

Thanks in advance.

---

### Post by Rubi1200 on 2010-08-10
Hi,
if you can use the live mode on Ubuntu from the USB then click on the link at the bottom of my post and follow the instructions there.

Post the results back here and please wrap the text with the code tag #

Thanks.

---

### Post by geekman314 on 2010-08-10
Firefox wont let me download it. Is it a script? Could you post it here so i could copy it into the terminal?

---

### Post by Rubi1200 on 2010-08-10
Yes, no problem. But you need to run it from a live environment, either the CD or USB.

---

### Post by geekman314 on 2010-08-10
Sorry If i sound stupid. I am not sure what you mean by a live usb/dvd. I have a usb drive in my computer that will let me install ubuntu, or try ubuntu.I am currently trying ubuntu so i can find help on the web. It says that there is 0 bytes left on the drive. And  firefox wont let me download anything. All i can do is read things on the internet.

---

### Post by geekman314 on 2010-08-11
Anybody else have any suggestions?

---

### Post by geekman314 on 2010-08-21
Okay. If any body reads this, I fixed it by getting the windows vista repair disc .iso from NeoSmart.com. I burned to a cd using the live ubuntu, and then fixed vista with it.

---

