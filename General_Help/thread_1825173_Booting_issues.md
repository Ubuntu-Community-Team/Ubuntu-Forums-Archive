---
title: "Booting issues"
date: 2011-08-14
forum: General Help
---

### Post by Quentin117 on 2011-08-14
Hello all.

I know next to nothing about ubuntu, but heres what's going on:

So i have a Toshiba Satellite laptop that came with Vista on it, i hated Vista so i found out about Ubuntu and had downloaded it on my old laptop with XP so i could test it out first (I dualbooted it and could easily switch from XP to ubuntu) so i figured i would dual boot it with my Toshiba ( originally a vista ). Well i have had ubuntu on this computer for about a year i'd say and i have loved it and never thought Vista, but now i kind of want to at least use it again, but i have no idea. On my other computer it would take me to GRUB and i could just pick..but on this computer it only lets me use ubuntu..

Is it possible that when i installed ubuntu it deleted vista?

Please help.

Edit: I am also sorry if this is in the wrong section.

---

### Post by Foxheadz on 2011-08-14
Yeah there is a big chance that you removed vista, you could try running ```
sudo update-grub
``` to refresh the grub menu if there was an other option. If that doesn't work then your gonna have to reinstall Vista if you reall ywant it

---

### Post by Quentin117 on 2011-08-14
> **Foxheadz said:**
> Yeah there is a big chance that you removed vista, you could try running ```
sudo update-grub
``` to refresh the grub menu if there was an other option. If that doesn't work then your gonna have to reinstall Vista if you reall ywant it

Hmmm....

Well i put grub on a flash drive and it's not even working, so i can't check to see if i deleted it for sure.

I get an error 'bootmgr is missing' beileve me, i've researched it and have been trying for hours and i just can't get it.

Any way to fix bootmgr error?

---

### Post by Foxheadz on 2011-08-14
uhh that would imply that there is no boot manager i believe, why did you put grub on a usb key? I meant just run it in a terminal

---

### Post by Quentin117 on 2011-08-14
I downloaded grub and moved it onto a usb..i thought thats how it works.

You put it on usb then restart computer and it should work..or thats how i did it on my XP.

I dont know how to do it any other way :O

---

### Post by Foxheadz on 2011-08-14
What exactly are you trying to do?

---

### Post by garvinrick4 on 2011-08-14
Can you still boot into Ubuntu on your Vista machine? If so open a terminal and run
```
sudo fdisk -l
``` (lower case L)
Post results.

---

### Post by Quentin117 on 2011-08-14
Basically....

I want to get vista back. I'm not sure if i still have it on this computer though after installing ubuntu.


So i want to use grub to check, since i know it will show me my OS that i can use.

But when i put grub on my flash drive...it says ''bootmgr is missing''.

Can you run grub in terminal?

---

### Post by garvinrick4 on 2011-08-14
Sorry foxheadz go ahead and fix em up, did not mean to interrupt your process.

---

### Post by Quentin117 on 2011-08-14
> **garvinrick4 said:**
> Can you still boot into Ubuntu on your Vista machine? If so open a terminal and run
```
sudo fdisk -l
``` (lower case L)
Post results.

Yes i am on the computer im talking about right now using ubuntu


Results: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008357c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23995   192737280   83  Linux
/dev/sda2           23995       24322     2621441    5  Extended
/dev/sda5           23995       24322     2621440   82  Linux swap / Solaris

Disk /dev/sdb: 2003 MB, 2003795968 bytes
62 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x73696d20

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      499280     1614184  2142844857    a  OS/2 Boot Manager
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(781, 103, 63) logical=(499279, 25, 34)
Partition 1 has different physical/logical endings:
     phys=(371, 68, 41) logical=(496865, 55, 7)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      141735      283470   272413365+  65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(370, 10, 16) logical=(141734, 56, 58)
Partition 2 has different physical/logical endings:
     phys=(288, 115, 51) logical=(283469, 14, 52)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?       43875       43875           0   65  Novell Netware 386
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(114, 111, 32) logical=(43874, 36, 51)
Partition 3 has different physical/logical endings:
     phys=(353, 115, 52) logical=(43874, 36, 50)
Partition 3 does not end on cylinder boundary.
/dev/sdb4          750698      750712       26464+   0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(750697, 30, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(750711, 16, 5)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by Foxheadz on 2011-08-14
Lmao no probelm garvin. Uhm just try booting normally and see if it works, if it does, try running ```
sudo update-grub
``` if you can no longer boot follow the link in my sig about restoring grub

---

### Post by garvinrick4 on 2011-08-14
##There is not a Windows install on this Hard Drive just Linux.
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008357c

   Device Boot      Start         End      Blocks   Id  System
[COLOR=Red]/dev/sda1   *           1       23995   192737280   83  Linux
/dev/sda2           23995       24322     2621441    5  Extended
/dev/sda5           23995       24322     2621440   82  Linux swap / Solaris[/COLOR]

---

### Post by Quentin117 on 2011-08-14
> **garvinrick4 said:**
> ##There is not a Windows install on this Hard Drive just Linux.
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008357c

   Device Boot      Start         End      Blocks   Id  System
[COLOR=Red]/dev/sda1   *           1       23995   192737280   83  Linux
/dev/sda2           23995       24322     2621441    5  Extended
/dev/sda5           23995       24322     2621440   82  Linux swap / Solaris[/COLOR]

So vista is gone?

---

### Post by Quentin117 on 2011-08-14
> **Foxheadz said:**
> Lmao no probelm garvin. Uhm just try booting normally and see if it works, if it does, try running ```
sudo update-grub
``` if you can no longer boot follow the link in my sig about restoring grub

Well the other fellow says that vista is not there from the results of what i got in the terminal...

So i guess i dont need grub anymore :O

---

### Post by garvinrick4 on 2011-08-14
> So vista is gone?
When you installed Ubuntu you selected to use whole disk at install.
No more Vista on this drive.

---

### Post by Foxheadz on 2011-08-14
No no you still do it lets you boot into ubuntu but you don't need it on a usb key. But if you still want vista follow this guide  [http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by garvinrick4 on 2011-08-14
While in Ubuntu what does this say open a terminal and copy and paste or type in:
```
grub-install --version
```

---

### Post by Quentin117 on 2011-08-14
> **garvinrick4 said:**
> While in Ubuntu what does this say open a terminal and copy and paste or type in:
```
grub-install --version
```

(GNU GRUB 1.98-1ubuntu12)

Well, the computer came with a vista recovery disk...i tried putting it in, i went to the BIOS and made it the first device to boot from, however it did nothing and went to ubuntu anyway. :l

---

### Post by garvinrick4 on 2011-08-14
You have a 200 gig disk and it does not have any Windows paritions on it at all.
You have a linux partition, a extended partition and a swap paritition.
If you want Windows have to install it off of your installation disk.
I imagine if you do will have problems with Ubuntu unless you follow a guide I believe
one was given to you in an earlier post 16 I believe.

---

### Post by Quentin117 on 2011-08-14
> **garvinrick4 said:**
> You have a 200 gig disk and it does not have any Windows paritions on it at all.
You have a linux partition, a extended partition and a swap paritition.
If you want Windows have to install it off of your installation disk.
I imagine if you do will have problems with Ubuntu unless you follow a guide I believe
one was given to you in an earlier post 16 I believe.


Ahhh...

Well thank you guys for you help :D

---

