---
title: "GRUB sees sda as hd1, sdb as hd0"
date: 2011-08-14
forum: General Help
---

### Post by Quatrix on 2011-08-14
As you can see below from the output of fdisk -l, I have a drive sda with a single Windows 7 partition and a drive sdb with the Ubuntu/GRUB partition and some other storage.  From this, I figured that GRUB would boot W7 /dev/sda1 as HD0 and Ubuntu /dev/sdb1 as HD1.  However, it's just the opposite.  In menu.lst, W7 is (hd1,0) and Ubuntu is (hd0,0).  If I try it the other way around then I get various errors.  Can anyone explain why it seems backwards?

Disk /dev/sda: 128.0 GB, 128035676160 bytes
242 heads, 36 sectors/track, 28704 cylinders
Units = cylinders of 8712 * 512 = 4460544 bytes
Disk identifier: 0x724fc7a9

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1   *           1       28704   125032448    7  HPFS/NTFS**

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc566bf2c

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1   *           1        4208    33800728+  83  Linux**
/dev/sdb2            4209       21832   141564779+  17  Hidden HPFS/NTFS
/dev/sdb3           21833      182401  1289770492+   f  W95 Ext'd (LBA)
/dev/sdb5           21833       29665    62918537    7  HPFS/NTFS
/dev/sdb6           29666      140627   891302218+   7  HPFS/NTFS
/dev/sdb7          140628      177179   293603899    7  HPFS/NTFS
/dev/sdb8          177180      182401    41945683+   7  HPFS/NTFS

title		Windows
root		**(hd1,0)**
savedefault
makeactive
chainloader	+1

title		Ubuntu 9.04
root		**(hd0,0)**
#kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=06a13bf6-c4ae-f755-da77-b640bdf8e014 ro quiet splash
kernel		/boot/vmlinuz-2.6.28-19-generic root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.28-19-generic
quiet

---

### Post by Elfy on 2011-08-14
Long time since I used grub rather than grub2 - but is there not another file in /boot/grub which says which drive is which. 

If you have no idea what I mean can you post the result of
```

ls /boot
ls/boot/grub
```

Please use code tags - [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end. 

What errors do you get if you change them then?

---

### Post by grahammechanical on 2011-08-14
Am I allowed two guesses?

a) The Ubuntu drive is plugged into the SATA number 1 socket on the motherboard and the Windows drive is plugged into the SATA number 2 socket of the motherboard.

b) You took the sensible precaution when installing Ubuntu of removing the Windows drive from the machine and now grub sees the Windows drive as a second drive and not a first drive.

Regards.

---

### Post by Quatrix on 2011-08-14
forestpiskie, you're probably thinking of device.map.  I already checked that:

(hd0)	/dev/sda
(hd1)	/dev/sdb

Regarding grahammechanical's guesses:

a) No, sda is on port 3 and sdb is on port 4 (1 and 2 are unused).

b) No, because everything used to be on the same physical drive.  sda is a new SSD to which I just moved Windows 7 from sdb2.

I thought that hd0 and sda are synonyms unles device.map says otherwise.  Is that not true?

---

### Post by Elfy on 2011-08-14
I was indeed :)

I assume that you edited the menu.lst to get the w7 on there. 

> If I try it the other way around then I get various errors.Like what?

I also assume that as it stands both boot correctly. 

Perhaps running the bootscript thing might shed a bit of light.  [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Edit - Found a 'similar' sort of issue elsewhere - might be worth a look [http://www.linuxquestions.org/questions/linux-general-1/an-interesting-grub-issue-875716/](http://www.linuxquestions.org/questions/linux-general-1/an-interesting-grub-issue-875716/)

---

### Post by Quatrix on 2011-08-14
> **forestpiskie said:**
> I assume that you edited the menu.lst to get the w7 on there. 

Like what?

It's been a while, but yes, I've done plenty of manual edits on menu.lst.

I don't remember the exact errors, but they were the ones you'd expect when pointing at the wrong boot loader, e.g. trying to load Ubuntu from a non-Ubuntu partition.

Thanks for the link.  I searched earlier but didn't find anything.  I'll take a look and follow up if needed.  Everything is working, so this isn't critical.  It just bugs me that the mapping isn't right.

---

### Post by Quatrix on 2011-08-21
From what I read today, the drive that GRUB/Ubuntu is booted from is automatically identified as hd0 regardless of the physical or BIOS order.  Someone correct me if I'm wrong.  That would explain the "wrong" mapping since my GRUB/Ubuntu drive was sdb.  Today I swapped the SATA ports so that the mapping is intuitive, with hd0 = sda and hd1 = sdb.

---

### Post by asomad on 2011-08-21
> **Quatrix said:**
> From what I read today, the drive that GRUB/Ubuntu is booted from is automatically identified as hd0 regardless of the physical or BIOS order.  Someone correct me if I'm wrong.  That would explain the "wrong" mapping since my GRUB/Ubuntu drive was sdb.  Today I swapped the SATA ports so that the mapping is intuitive, with hd0 = sda and hd1 = sdb.

I'd love to know also... I almost chimed in with, "nowadays, many bios utilities allow you to set the boot priority (ie. assign drive #s manually) when you have multiple HDDs, so that the bios know which HDD it wants when it gets to the HDD on its boot-up device order.." blah blah, oh I just said it.

---

