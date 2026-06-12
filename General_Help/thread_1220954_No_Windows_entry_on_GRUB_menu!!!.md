---
title: "No Windows entry on GRUB menu!!!"
date: 2009-07-23
forum: General Help
---

### Post by QueenZ on 2009-07-23
Hello
I installed Kubuntu 9.10 Karmic Koala Alpha 3 and my Windows 7 entry disappeard from the GRUB menu list and i'm wondering how i can get it back.. please help!

---

### Post by nikhilk on 2009-07-23
> **QueenZ said:**
> Hello
I installed Kubuntu 9.10 Karmic Koala Alpha 3 and my Windows 7 entry disappeard from the GRUB menu list and i'm wondering how i can get it back.. please help!

Post the output of
```
sudo fdisk -l
```
and contents of your "/boot/grub/menu.lst" file
```
sudo cat /boot/grub/menu.lst
```

---

### Post by QueenZ on 2009-07-23
> queenz@queenz-laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40c132b1                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5826    46797313+   7  HPFS/NTFS
/dev/sda2            5827        7296    11807775    5  Extended 
/dev/sda5            5827        7172    10811713+  83  Linux    
/dev/sda6            7173        7296      995998+  82  Linux swap / Solaris

Disk /dev/sdb: 2041 MB, 2041577472 bytes
63 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0xb0bcd68e

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      825235      888389   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(825234, 44, 50)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(888388, 51, 15)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      110823      309410   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(110822, 6, 14)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(309409, 54, 34)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      478639      969993   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(478638, 40, 56)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(969992, 62, 35)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      347110      349241     4161546+   a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(347109, 16, 23)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(349240, 6, 49)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


> queenz@queenz-laptop:~$ sudo cat /boot/grub/menu.lst
[sudo] password for queenz:

title UNetbootin-ubuntu804rev99
root (hd0,4)
kernel /boot/ubnkern vga=normal
initrd /boot/ubninit
boot


hmm.. ..

---

### Post by nikhilk on 2009-07-23
The following line says that you Windows bootable partition is the first partition of your first hard drive
```
/dev/sda1 * 1 5826 46797313+ 7 HPFS/NTFS
```

And your menu.lst says that you only have one option at boot time viz. UNetbootin-ubuntu804rev99, is this correct?

To add boot option for Windows XP add these line at the end of your /boot/grub/menu.lst file and reboot. You should see an additional entry "XP" which should boot into Windows.
```
title XP
root (hd0,0)
savedefault
makeactive
chainloader +1
```

Let us know if this works for you.

---

### Post by Zorael on 2009-07-23
[FWIW](https://wiki.kubuntu.org/KarmicKoala/Alpha3/Kubuntu#Known%20Issues);
> [SIZE="4"][COLOR="DeepSkyBlue"]Known Issues[/COLOR][/SIZE]
[list][*]If you install Karmic Alpha 3 alongside Windows, the grub boot menu may not offer to start Windows. ([402795](https://bugs.launchpad.net/bugs/402795))
[*]The Kubuntu Netbook Edition is missing the "install" icon on the desktop. You can start the installation from the menu. ([402878](https://bugs.launchpad.net/bugs/402878))
[*]The Kubuntu Netbook Edition image does not install under Windows (with wubi). ([402850](https://bugs.launchpad.net/bugs/402850))[/list]

[Comment #7 of lp#402795](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/402795/comments/7):
> I've just installed Karmic Koala alpha 3 and had the same problem, ie Windows not showing up in grub menu. I just ran '**sudo update-grub2**' and that fixed the problem. Guess there is a bug in the installer.

---

### Post by QueenZ on 2009-07-23
Thanks, it should work now! :) I'll get back to you if it doesn't!

> queenz@queenz-laptop:~$ sudo update-grub2
[sudo] password for queenz:
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-3-generic
Found initrd image: /boot/initrd.img-2.6.31-3-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done

---

### Post by alexzeit on 2009-07-27
I installed Karmic server 64 bit edition, and have the same problem with grub.Before On the first partition I had Windows XP and it is not in the Grub menu.
I tried:
```
sudo update-grub2
```Output:
```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-3-server
Found initrd image: /boot/initrd.img-2.6.31-3-server
Found memtest86+ image: /boot/memtest86+.bin
done

```.. and there is no menu.lst in /boot/grub/

Any help would be highly appreciated

---

### Post by alexzeit on 2009-07-27
Solution:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/402795/comments/14](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/402795/comments/14)

---

