---
title: "Intel RAID Controller - Ubuntu showing 2 drives?"
date: 2010-04-24
forum: General Help
---

### Post by danioj on 2010-04-24
Hello everyone,

I shall start off by saying that I have just jumped from Windows 7 to Ubuntu and am not regretting the decision one bit.

I am however stuck with a problem. I have spent a few hours google'ing this and have read some interesting articles (probably way beyond what the problem actually is) but still don't think I have found the answer.

I have installed:

Distributor ID:    Ubuntu
Description:    Ubuntu lucid (development branch)
Release:    10.04
Codename:    lucid

I am running the install on an old Dell 8400. My PC has an Intel RAID Controller built into the MB. 

I have 1 HDD (without RAID) (which is houses my OS install) and then I have 2 1TB drives (These are just NTFS formatted drives with binary files on them nothing more.) in a RAID 1 (Mirroring) Array.

The Intel RAID Controller on Boot recognizes the Array as it always has (irrespective of which OS is installed) however, unlike Windows 7 (where I was able to install the Intel RAID controller driver) ... Ubuntu recognizes both drives as separate!?

Does anyone know of a resolution (which doesn't involve formatting and / or use of some other software RAID solution) - to get this working which my searches have not taken me too?

Thank you in advance for your time reader!! 

Daniel

---

### Post by danioj on 2010-04-24
Well .... in the true spirit of things I am having a go myself! LOL!

I have just installed dmriad and done a reboot.

It has done something, as the 2 drives have now "disappeared" from the Places Menu.

However, my babies are of course still there:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000128d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29651   238164992   83  Linux
/dev/sda2           29651       30402     6031361    5  Extended
/dev/sda5           29651       30402     6031360   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe5b8c9b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe5b8c9b9

And now I am stuck again, I have done a dmriad -r and got the following:

dan@dans-desktop:~$ sudo dmraid -r
/dev/sdb: isw, "isw_dihiiadcac", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sdc: isw, "isw_dihiiadcac", GROUP, ok, 1953525166 sectors, data@ 0

From my reading I am thinking it has something to do with mounting a folder from within /dev/mapper

Mine reads:

dan@dans-desktop:/dev/mapper$ cd /dev/mapper/
dan@dans-desktop:/dev/mapper$ ls
control  isw_dihiiadcac_Storage  isw_dihiiadcac_Storage1

But unfortunately there are 2 ... and I only want to mount 1!

LOL ... back to stuck!

---

### Post by danioj on 2010-04-29
Looks like I was on the right track.

Of the two, only one of them had a mountable partition. Which just so happened to be the one appended with the number.

If there had been more than 1 partition on the drive , there would have been more iterations (i.e. Stroage2, Storage 3 etc.)

I hope this helps someone in the future, but all is good here and working now! =:-)

---

