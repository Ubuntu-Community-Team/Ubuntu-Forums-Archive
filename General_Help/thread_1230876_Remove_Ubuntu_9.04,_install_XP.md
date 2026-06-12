---
title: "Remove Ubuntu 9.04, install XP"
date: 2009-08-03
forum: General Help
---

### Post by BlueMana on 2009-08-03
Hey guys,

I've searched the forums, but haven't seen my question answered...

I have a system that has Ubuntu 9.04 installed in a single partition.

What I'm trying to do is completely remove Ubuntu, and install XP onto the drive.

Every time I boot to the XP CD, setup tells me it cannot find the hard drive.  I assumed this was because of the ext3 file system Ubuntu was using.

I booted to a LiveCD of GParted, and removed all partitions in an attempt to start from scratch, but no luck.

Anything obvious that I'm doing wrong?  I'm very much a novice when it comes to Ubuntu, so any help would be greatly appreciated!

PS: I'm not giving up on Ubuntu, I just need to use XP on this one drive, I still have Ubuntu on another system...

Thanks!

---

### Post by nhanquy on 2009-08-03
Boot LiveCD again. Use Gparted to format the NTFS (or FAT32) partition, flag it as boot device.
Then install XP again. It should work.

---

### Post by darolu on 2009-08-03
GParted should do it, you are probably forgetting to click on "apply" or something like that; make sure to deactivate swap before deleting it or you won't be able to do it.

Anyways, you can also try with Parted, here is a quick tutorial: [http://linux.about.com/od/commands/l/blcmdl8_parted.htm](http://linux.about.com/od/commands/l/blcmdl8_parted.htm)

---

### Post by razorboy5 on 2009-08-03
it may be because windows XP does not automatically detect SATA drives. 

Meaning that if u have a SATA hard drive u need a floppy disk with SATA drivers installed for XP to recognize the hard drive and properly install

i've had this problem when trying to install XP for a dual boot

if u dont have a floppy drive installed there is a simple solution on google

---

### Post by balaknair on 2009-08-03
Most likely cause- XP won't detect SATA drives without the drivers.

Solution- 
either turn SATA mode(also called AHCI mode in some models) off in BIOS(switch to IDE mode) 

or use a floppy to load the drivers during install(you will be asked to hit F6 to load drivers while XP is loading during boot from the CD)

or slipstream the XP SATA drivers into a custom XP install CD.
[http://www.digitgeek.com/how-to-slipstream-sata-drivers-into-xp-cd/](http://www.digitgeek.com/how-to-slipstream-sata-drivers-into-xp-cd/)

The last two assume that you can get the appropriate drivers from your motherboard manufacturer(Intel or ASUS or whatever).

---

