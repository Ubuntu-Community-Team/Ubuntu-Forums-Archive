---
title: "grub2 does not detect my partition"
date: 2010-05-09
forum: General Help
---

### Post by rahilm on 2010-05-09
booting 4m external it goes into rescue mode saying uknown partition
wen i boo 4m computer grub it says no such device.
Cannot even browse via grub command line. Says unknown partition.
Posting via mobile

---

### Post by rahilm on 2010-05-09
does a solution exist ?
Should i give up hope ?

---

### Post by efflandt on 2010-05-09
Is that a full installation on 4 GB USB (bootable live/install iso on USB does not usually use grub)?  What type of file system is it on?  Which Ubuntu version?  Did you install grub2 to that device, or is that using grub2 on your main hard drive?  What computer motherboard?

The release note link below explains one possible issue/fix in 10.04 LTS that can result in a grub rescue prompt following **error: unknown filesystem** or **error: file not found** due to a change in the way 10.04 aligns partitions.  I had that issue initially trying 10.04 on USB hard drives with my HP a530n and that resolved it.  Other computers had no issue booting the USB drives before I fixed them.

See [http://www.ubuntu.com/getubuntu/releasenotes/1004#Partition%20alignment%20changes%20may%20break%20some%20systems](http://www.ubuntu.com/getubuntu/releasenotes/1004#Partition%20alignment%20changes%20may%20break%20some%20systems)

---

### Post by rahilm on 2010-05-10
I am still on mobile so i can't explain much..
I have a 250 Gb externel hard disk with a 20gb ext4 partition at the end of it where ubuntu 10.04 is installed. . . It booted 5n on my PC but it doesn't boot on my cousin's.
I guess it has something to do with BIOS limitation..

(i google grub unknown partition non-first partition)

i don't think anything can be done because the partition is listed but not browsable via grub command line of d internal hard drive..

---

### Post by Mark Phelps on 2010-05-10
It would help if you disable autocomplete on your mobile ... that way, when you type "fo..." it would not insert "4' and when you type "fi ..." it would not insert "5".

---

