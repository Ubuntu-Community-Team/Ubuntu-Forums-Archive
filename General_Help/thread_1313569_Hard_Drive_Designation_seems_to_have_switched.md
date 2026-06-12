---
title: "Hard Drive Designation seems to have switched"
date: 2009-11-03
forum: General Help
---

### Post by DocEsq on 2009-11-03
I have Ubuntu 8.04 installed on an 80Gig IDE drive.  I then installed XP on a second IDE drive.  Grub was set up using the Linux drive as Hd0 and XP as HD1.  Everything boots perfectly with the Linux drive booting first in as per the BIOS.  I then added a SATA drive for shared storage.

When I check in the XP Disk Management I get the following:

Disk0 is the Sata drive
Disk1 is the Ubuntu drive
Disk2 is the XP drive

This correlates to what I get in Partition Editor (Gpart):
Sda (SATA drive)
Sdb (Ubuntu drive)
Sdc (XP drive)

Since I had set up grub to:
root (hd0,0)
Setup (hd0)

Thinking my Ubuntu drive was the first drive in which I needed to load grub to, how come the Ubuntu drive is now Sdb or Disk1 and how come grub is loading properly?

I maybe missing something here but I am not sure what.

Any explanation will be appreciated.

Thanks.

DocEsq

---

### Post by louieb on 2009-11-03
Near as I can tell a drive is designated to be sda, sdb, ... by where it is physically plugged in.  To confuse matters more some motherboards/BIOS will list ide drives first then sata. While others list sata drives 1st. 

GRUB goes by boot order as reported by BIOS:  1st drive in boot order is hd0 , 2nd drive hd1 ... Change the boot order in BIOS and you can see where that could lead to problems.

Anyway most of the time sda and hd0 would be the same drive. But not always.

From the [GNU GRUB Manual 0.97]("http://www.gnu.org/software/grub/manual/grub.html") setcion on grub-install
> 
**Caution:** This procedure is definitely less safe, because there are several ways in which your computer can become unbootable. For example, most operating systems don't tell GRUB how to map BIOS drives to OS devices correctly—GRUB merely guesses the mapping. This will succeed in most cases, but not always. Therefore, GRUB provides you with a map file called the device map, which you must fix if it is wrong. See [Device map]("http://www.gnu.org/software/grub/manual/grub.html#Device-map"), for more details.     


Be glad yours works.

---

