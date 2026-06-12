---
title: "Problem with GRUB after Seagate FreeAgent drive was used"
date: 2010-03-01
forum: General Help
---

### Post by jmsc1990 on 2010-03-01
Hello,

I have a dual boot PC with Windows Vista and Ubuntu 9.1.  The problem did start with Ubuntu 9.04.  I think the problem started around the same time I added a Seagate FreeAgent USB hard drive for backups.

The GRUB OS list will come up after the PC boots.  I can select Vista and it will start w/o a problem.  If I try to boot to Ubuntu the PC will restart itself.  It may try and start Ubuntu MANY times until it eventually gets started.  

I have tried to repair the problem with no results so far. I have tried it with and without the Seagate device attached.

My hard drive list looks like.....

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68b07f2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         892     7164958+  12  Compaq diagnostics
/dev/sda2   *         893       24589   190344588    6  FAT16
/dev/sda3           24590       38913   115057530    5  Extended
/dev/sda5           24590       38325   110334388+  83  Linux
/dev/sda6           38326       38913     4723078+  82  Linux swap / Solaris

---

### Post by bobcollard on 2010-03-01
> **jmsc1990 said:**
> Hello,

I have a dual boot PC with Windows Vista and Ubuntu 9.1.  The problem did start with Ubuntu 9.04.  I think the problem started around the same time I added a Seagate FreeAgent USB hard drive for backups.

The GRUB OS list will come up after the PC boots.  I can select Vista and it will start w/o a problem.  If I try to boot to Ubuntu the PC will restart itself.  It may try and start Ubuntu MANY times until it eventually gets started.  

I have tried to repair the problem with no results so far. I have tried it with and without the Seagate device attached.

My hard drive list looks like.....

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68b07f2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         892     7164958+  12  Compaq diagnostics
/dev/sda2   *         893       24589   190344588    6  FAT16
/dev/sda3           24590       38913   115057530    5  Extended
/dev/sda5           24590       38325   110334388+  83  Linux
/dev/sda6           38326       38913     4723078+  82  Linux swap / Solaris
PLEASE READ ALL OF THIS FIRST:
Was your Seagate attached at the time you installed each system?  I found a bug that is caused by Ubuntu installing part of grub on the other HD and the confusion reigns.  My solution was to backup everything up off the Seagate onto my internal HD then reformat the Seagate.  Moving everything back, unplugging the Seagate and reinstalling the system, not the Windows, just the Ubuntu.  The Seagate probably is formated for FAT32, that seems to be their main format.  Keep it, both systems can read and write to it.  An alternative might be unplug the Seagate and open terminal in Ubuntu then type in "sudo update-grub" (without quotes)  Wait for it, it takes awhile.  Even then you may have to reformat the Seagate but you will save some time and settings.

---

### Post by jmsc1990 on 2010-03-02
I'll give it a try when I get back home tomorrow.

The OSes were installed first and the pc (both Ubuntu and Vista) were very stable.  I added the Seagate about a month ago and that is when the problems began.

Thanks!!

---

### Post by bobcollard on 2010-03-02
I have two Seagates the I use on my laptop, both USB.  Both are 250GB, one runs off of house current and I have another system (BSD) on that.  The other is a portable running off of USB current and it is my main backup.  I chose Seagate for the second one because that brand worked on the first model.  I've had no problems with either one that I did not create myself.  I have reformatted both at one time or another.

---

