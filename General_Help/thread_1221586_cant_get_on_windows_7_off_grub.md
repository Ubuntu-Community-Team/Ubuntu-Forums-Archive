---
title: "cant get on windows 7 off grub"
date: 2009-07-24
forum: General Help
---

### Post by madking247 on 2009-07-24
hey guys i am new to Ubuntu trying it out, and its fantastic so far no problems, but i cant access my windows.

now here is my fdisk -l 
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7fca7fca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       60476       60801     2618595   82  Linux swap / Solaris
/dev/sda2               1       60475   485765406    f  W95 Ext'd (LBA)
/dev/sda5           10200       60475   403841932    7  HPFS/NTFS
/dev/sda6               1       10199    81923373   83  Linux

Partition table entries are not in disk order

```my windows is located in sda5


i edited my grub menu.lst and put 
```

title              windows
rootnoverify       (hd0,5)
chainloader        +1

```now i see it in the boot loader i select windows-enter. it says stage 2 loading then goes back to the grub screen.  

i also ran windows 7 cd did repair computer didnt work. now i can access my files i have to mount the harddrive which is 413gigs. but i would like to get on windows 7.

so if anyone has any ideas that will get it to work, that will be greatly appreciated.

thanks
madking
*edit - i also did root (hd0,5) and setup root (hd0,5)*

---

### Post by tkawa6 on 2009-07-24
give this a try.

> title Windows
root (hd0,4)
chainloader +1
savedefault
makeactive

---

### Post by madking247 on 2009-07-24
Unfortunately, that method did not work when i try entering windows i get
Error 12: invalid device requested.

---

### Post by merlinus on 2009-07-24
It looks like you installed win7 in a logical, not primary partition, and that may be causing your problems.

---

### Post by madking247 on 2009-07-24
alright so what can i do? i could reinstall but who wants to sit through that?

---

### Post by merlinus on 2009-07-24
Someone may have a better idea, but you would have to use gparted to shrink and then move partitions to change win7 to a primary, and that would take hours.

If you do not have lots of data to back up, starting over is better than teeth gnashing and hairpulling.  But if you decide to start over, do some research and plan your partitions beforehand.

For example, create a primary partition that is the first one on the hdd, and install 7 into that.  Then create an extended partition for the rest of the hdd, because linux is happy living in a logical.  

You might then also create a separate logical partition for /home, which is where your personal data and application configurations are stored.  This will make reinstalling and/or installing a newer version of ubuntu much easier.

And you mght also create an ntfs partition for sharing data between both operating systems.

---

### Post by madking247 on 2009-07-24
alright thx man well ill do that in a couple of days does anyone else have any idea?

---

