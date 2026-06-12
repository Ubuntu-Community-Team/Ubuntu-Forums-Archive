---
title: "Having trouble detecting my other Ubuntu Partition."
date: 2010-04-25
forum: General Help
---

### Post by Daners on 2010-04-25
Alright, so I had Ubuntu installed, and then I installed windows 7, which messed up my boot loader so I couldn't get back into Ubuntu. So what I did was Installed Ubuntu again thinking that I could just transfer the files from my first Ubuntu install into the new one and then just format the old partition and extend the new Ubuntu partition. So, after I installed Ubuntu the second time, it fixed the boot loader and when I boot up I can choose between Windows 7 and Ubuntu. However, when I look in Gparted, it only shows my "new" Ubuntu partition, and the Partition I made for Windows 7. My HD is something like 330gb, but on Gparted it shows it as only being 298gb, meaning that old Ubuntu partition is still there apparently, but I can't see it on Gparted in order to format it and get rid of it, nor can I access it to get the files I have in it. Anybody have any ideas on what I can do about this? (If worst comes to worst, I can just leave it as is, I'm not going to need that 30gb of space anytime soon, but it would be nice to get the files I have saved there if at all possible).
Thanks in advance
Daners

---

### Post by themusicalduck on 2010-04-25
When you bought your hard drive was it advertised as being 330gb?

There is an annoying con by hard drive companies to refer to 1 gigbyte as 1000 megabytes when labelling a hard drive. In reality there is actual 1024 megabytes in a gigabyte. This means that your hard drive is not actually what they say it is but slightly less.

For instance my 160gb drive is actualy 149 and my 1TB drive is 931 :|

If it  did show as being 330 in gparted before and is now showing as less, then something might be up. I'm not sure what.

Also for future reference, there is an easier way of re-installing grub detailed here - [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

---

### Post by oldfred on 2010-04-25
Part of the difference is the hard drive mfgs as themusicalduck says, but part maybe due to journaling of the hard drive. Journal allocate space in advance and you do not see it.

If you run this do you see additional partitions?

```
sudo fdisk -l
```

---

### Post by Daners on 2010-04-25
This is what shows up in the terminal:

Disk /dev/sda: [COLOR=Red]320.1 GB[/COLOR], 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec1565b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5117    41102271    7  HPFS/NTFS
/dev/sda2           26108       38913   102864195    5  Extended
/dev/sda3            5118       26107   168602175    7  HPFS/NTFS
/dev/sda5           38162       38913     6040408+  82  Linux swap / Solaris
/dev/sda6           26108       37665    92839572   83  Linux
/dev/sda7           37666       38161     3984088+  82  Linux swap / Solaris

(Ps I made 2 Windows partitions, one being about 40gb, for program file etc. and another thats about 160gb for other files.) Does this look right? Does it look like I just deleted the old Ubuntu partition? I think it was roughly 20-30gb when I made it).

---

### Post by oldfred on 2010-04-26
Yes it looks like there is only one linux partition. You still have two swaps, but need to be sure which is used by your current install so you do not delete the wrong one. /etc/fstab has the swap entry.

sudo blkid will tell you the UUID that fstab has for your swap entry.

---

