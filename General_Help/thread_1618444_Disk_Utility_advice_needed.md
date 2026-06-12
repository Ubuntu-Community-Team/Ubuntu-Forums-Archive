---
title: "Disk Utility advice needed"
date: 2010-11-10
forum: General Help
---

### Post by op3studios on 2010-11-10
greetings Ubuntites,


I'm not giving up.
just rearranging things so I'm not shut down while learning Linux stuff.  it's Ubuntu on a PC; so it must be my fault.

presently, I have a buggy 10.10 on my single partition 90GB ssd.
Shotwell won't load.  when I call File Browser from the GUI, Rhythm Box launches....lol.  (no, I mean really, lol.)

but I'm staying.

please advise best disk management tool.  the one in Ubuntu 10.10 seems a bit limited to my wandering eye, and I need a traveling Nuclear Option utility disk anyway I can boot from any machine.
is Hirems Boot Disk still the thing?

I want to 

1.  isolate the active Ubuntu partition intact @ 20GB.

2. create a NTSF partition for W7 @ 20GB.

3. create a data partition of the remainder that can be used as an in progress data transfer store for ongoing work that can be well accessed by both Ubuntu and W7.  what file format is best for this swapping?  I need more capability than FAT. I'm thinkin NTSF.


4.  my SATA data drive remains unaccessible after the Shotwell crash described last post.  I'll deal with this once I have my production capability configured in W7.  I'm hoping to restore it intact.

I intend to use Ubuntu for everything but final Studio production stuff.  for that it's still W7 and Adobe.

note to switcherooners:
dual boot for now till you get proficient with Linux Terminal and don't have to think everything through.  the Ubuntu 10.10 GUI is really nice, but it's the Terminal that continues to wear the gun.  

Jim

don't bother telling me I'm crazy,
I already know.

---

### Post by Hippytaff on 2010-11-10
I know the answer to question 3 and so did you...ntfs :-)

thats about all I can offer you though :-)

---

### Post by op3studios on 2010-11-10
hmmm....

can't get CD Creator to write an .iso.
just dumps.

if someone illuminates the way, I'll do it via Terminal.



think I'll wire up my K8V and do a clean install on this machine at this point.  It's a New Day!

still want to partition as above with best utility tho.

And, 
what's the best utility program for backing up my present Ubuntu install before striking a match.  (not whole partition bak...

for clean install on single disk, multiple partitions, does Windows need to be installed first?

Jim

---

### Post by efflandt on 2010-11-10
I am still mystified by the default Disk Utility.  I once tried to mark a partition as the boot partition and it endlessly started thrashing my drive.

I would suggest using **gparted** (not installed by default, but is on live/install CD or bootable USB).  You cannot repartition a drive you are running from anyway, so I would use gparted from install iso on CD or USB.  On that it will be under System > Adminstration > Gparted.

One problem with installing Windows after installing Ubuntu is that the Windows installation will wipe out grub in your mbr.  So have instructions handy for restoring grub2 [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

For the other partition accessibly to Win7 or Ubuntu, I would just create that as NTFS.  Linux has no problems using that (as long as it is a regular NTFS partition and not part of a Windows dynamic volume).

Once you get Win7 up on your ssd you could use that to **chkdsk /f** your other Windows partition.  But it will have a different drive letter than c: when it is not the partition Win7 booted from.

---

### Post by op3studios on 2010-11-10
Sir,

after dispensing this praise
I am off to the races.
thanks
JHS

---

