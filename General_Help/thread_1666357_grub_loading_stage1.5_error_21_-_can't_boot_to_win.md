---
title: "grub loading stage1.5 error 21 - can't boot to win7 nor ubuntu"
date: 2011-01-13
forum: General Help
---

### Post by doron387 on 2011-01-13
well, after hours of trying i give up and ask you guys, can any body help me ?

machine : asus 1201n
original os : win7
another os : ubuntu 10.10 inside wubi

the event :
i have installed backtrack 4 final into a usb pendrive, using the win7 os.
after the process i get every time that i turn on the machine the same message :
[COLOR="Navy"]GRUB Loading stage1.5
GRUB loading, please wait...
Error 21[/COLOR]

i have tried :
1. installed Windows 7 Recovery Disc onto a usb pendrive and booted from it, tried automatic recovery, no help, same error.
2. tried ubuntu live cd on a pendrive. bootod off it, sudo grub and all kinds of offers that were on the web, but nothing worked.

sould i fix the grub or the mbr ? (and i actually don't really understand the difference between them and don't know to fix either of them)

thanks ahead

doron387

---

### Post by Hippytaff on 2011-01-13
Have you had a look at the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198")?

---

### Post by bcbc on 2011-01-13
> **doron387 said:**
> well, after hours of trying i give up and ask you guys, can any body help me ?

machine : asus 1201n
original os : win7
another os : ubuntu 10.10 inside wubi

the event :
i have installed backtrack 4 final into a usb pendrive, using the win7 os.
after the process i get every time that i turn on the machine the same message :
[COLOR="Navy"]GRUB Loading stage1.5
GRUB loading, please wait...
Error 21[/COLOR]

i have tried :
1. installed Windows 7 Recovery Disc onto a usb pendrive and booted from it, tried automatic recovery, no help, same error.
2. tried ubuntu live cd on a pendrive. bootod off it, sudo grub and all kinds of offers that were on the web, but nothing worked.

sould i fix the grub or the mbr ? (and i actually don't really understand the difference between them and don't know to fix either of them)

thanks ahead

doron387

It sounds like you installed grub (legacy) to your internal drive MBR. Just replace it with a windows bootloader. That link from Hippytaff to the Wubi megathread explains how.

If this doesn't work, post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

---

### Post by doron387 on 2011-01-14
thanks guys,
i have read what you offered, but a little bit confused of both offers.
i'll try to clarify my situation :
1. when i power on machine with no pendrive connected - i get the grub loading sttage 1.5, grub error 21.
and it stays like this forever (i assume that it means that while previously i installed backtrack-4 to another pendrive, it installed grub in it and now the system, when loading is looking for it but can't find it so it hangs)
2. when i power on the machine with a pendrive (E:) connected (it has multiboot-iso installed in it with some distros)it gives me the options to boot into windows 7 and to the wubi install.
3. when i am inside windows 7, and open EasyBCD software it says: 
[COLOR="RoyalBlue"]There are a total of 2 entries listed in the bootloader.

Default: Windows 7 Home Premium (recovered) 
Timeout: 30 seconds
Boot Drive: E:\

Entry #1
Name: Windows 7 Home Premium (recovered) 
BCD ID: {current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.exe

Entry #2
Name: ubuntu 10.10 in wubi
BCD ID: {hgfkgkhjglhglhglhblgghblyglhbllhbl}
Drive: C:\
Bootloader Path: \NST\AutoNeoGrub1.mbr[/COLOR]

*** i thing that it installed the grub in E: ***
how do i move it to the right place so i could boot stright from my hd ?

thanks
doro387

---

### Post by bcbc on 2011-01-14
grub legacy is in your drive MBR, but then it looks on the pendrive for it's boot files. That's why it fails to boot when it's not plugged in.

You need to install the grub legacy bootloader on the pendrive, and windows' bootloader on the internal drive. 

To do the former, see [COLOR="DarkRed"]How to restore the Ubuntu grub bootloader (9.04 and older)[/COLOR] on this thread: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708). 
On the same thread it shows how to reinstall the Windows bootloader - for windows 7 you just need "bootrec.exe /fixmbr" (ignore the /fixboot command)

---

### Post by doron387 on 2011-01-14
hi bcbc,
1. i have been reading this thread for hours, trying all kinds of stuff of it, but without understanding exactly what i am doing.
2. wheni boot to my machine with a different ubuntu on a stick (like right now) and type fdisk -l i get the following :

[COLOR="RoyalBlue"]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x593e9087

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13055   104857600    7  HPFS/NTFS
/dev/sda2           13055       37606   197208064    7  HPFS/NTFS
/dev/sda3           37606       38911    10485760   1b  Hidden W95 FAT32
/dev/sda4           38911       38913       16224+  ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x58f8a4bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         977     7841248    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(975, 254, 63) logical=(976, 49, 32)
ubuntu@ubuntu:~$ [/COLOR]

3. to clarify it again (for myself also, if you don't mind) :
i think that the grub was installed on the pendrive that is not the one that is connected right now.
i don't have the smallest clue what to do.
will you please lead me from this point ?

i am waiting, connected to ubuntu live usb on the problematic machine.

thanks
doron387

---

### Post by doron387 on 2011-01-14
hey bcbc,

i was non patient, as most of us probably....lol

and tried from the thead that you pointed me (wubimegathread) the folloing :
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

now my machine works as it was before lol lol lol :D

would you give me a hint what was the problem and what was the fix please ?

doron387

---

### Post by bcbc on 2011-01-14
If you ran that bootinfoscript I linked to (instructions within) it would tell you that /dev/sda has grub in it's MBR and it points to /dev/sdb1 (the partition on your pendrive that's not present at the moment). You should probably run that script to check this.

/dev/sda has no linux partitions and requires a Windows bootloader (or equivalent) to boot. There is an efi partition - sometimes that overides the MBR - not sure about that.

But to install the windows bootlaoder in the master boot record on /dev/sda you need to follow the instructions I gave.

You can also use a windows equivalent bootloader (lilo) and install it right from Ubuntu. To do this:
```
sudo apt-get install lilo
```
(Hit ENTER on OK on the big warning screen that you can ignore despite the severe warnings as it relates to using lilo to boot linux).
Then install lilo to the MBR:
```
sudo lilo -M /dev/sda mbr
```

---

### Post by doron387 on 2011-01-14
thnx,
worked,
doeon387

---

### Post by bcbc on 2011-01-14
> **doron387 said:**
> thnx,
worked,
doeon387

cool if you boot your wubi install and run "sudo update-grub" while your pendrive is plugged in, it will probably find backtrack and add it to the wubi grub2 menu. Then you can boot it from there.

---

