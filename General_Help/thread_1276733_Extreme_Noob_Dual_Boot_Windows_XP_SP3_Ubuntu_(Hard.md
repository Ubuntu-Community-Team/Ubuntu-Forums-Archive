---
title: "Extreme Noob Dual Boot Windows XP SP3/ Ubuntu (Hardy Heron )"
date: 2009-09-27
forum: General Help
---

### Post by missygail on 2009-09-27
I recently took my computer to U of H and had a dual boot installed. My Recently Deceased husband was working on it until he passed (he was employed there), I am now having problems on both side of the system (Hardy Heron and WinXP SP3). On the ubuntu side i am getting 

ERROR 18: Selected cylinder exceeds maximum supported by Bios  

Press any key to continue...

/dev/sda5 contains a file system with errors,
check forced



Ont the winXP SP3 side I am getting
DRIVER_IRQL_NOT_LESS_OR_EQUAL

Disable or remove any newly installed hardware or software

Disable BIOS memory options such as caching or shadowing 

Using SafeMode to remove or disable components,restart computer,pressF8 to get advanced startup option then select SafeMode

Tech info
STOP: 0x000000D1  (0xB2532000,0X00000002,0X00000000,0XB9AC60D8)

viahduaa.sys- addresse B9AC60D8 base at B9A9E000 Datestamp 4a24e854

Begging dump of physical memory
Physical memory dump complete

my son also uses the winxp and got a similar message but some of the nubers were different.

If anyone could point me in the right direction or offer any type of help it would be greatly appreciated.

---

### Post by quixote on 2009-09-28
First, if you can, get any data you care about backed up onto removable media, or somewhere accessible on the network, if the computer is networked.

On the Windows side, it sounds like it needs the Master Boot Record fixed.  Boot from a Windows Recovery CD (or any external bootable medium, even a bootable DOS floppy if the machine is old enough to have a floppy drive).  At the command prompt, type ```
fixmbr
```

That should fix the Windows, but will remove grub, which is the bootloader that gives you the choice of operating systems when you begin.  Grub is what's giving you the "Error 18."  That error usually occurs with older machines that have older BIOS, but have had a newer and much larger hard drive put in.  The old BIOS doesn't understand the size of the new drive, hence the "selected cylinder exceeds the size" message.

The fix for that is to repartition the drive into smaller chunks.  If you have a lot of free space on either the ubuntu or the windows partition, that's not difficult to do.  Boot from an ubuntu LiveCD, go to System > Administration > GParted (for Gnome Partition Editor).  (At this point, it is definitely a Good Thing to have important data backed up.)  Shrink the largest partition(s).  That will create "free space".  Create a new partition(s) in the free space.  You might want to use it as a data partition that is accessible to both operating systems, in which case "fat32" is one of the types that can be read by both.

To fix grub, boot from a LiveCD.  (If you've repartitioned, as per previous paragraph, then reboot from the LiveCD.) 

Open a terminal (Start > Accessories > Terminal), and type ```
grub
```This gives you a (I'm sure you're surprised :) ) grub prompt.  Then type```
grub> find /boot/grub/stage1 *(will output a partition name like (hd0,3) )*
grub> root (hd0,3) *(substitute the right numbers for 0,3)*
grub> setup (hd0,3) *(again, substitute as necessary for 0,3)*
grub> quit
```Close the terminal and restart the system, and remove CD when prompted to.

If it all worked, you'll have Windows and grub giving you the choice to boot into Ubuntu.

---

