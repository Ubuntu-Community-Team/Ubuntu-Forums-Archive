---
title: "Copy entire Jaunty disk to external HDD"
date: 2009-11-12
forum: General Help
---

### Post by von Stalhein on 2009-11-12
I want to copy my entire drive to an external HDD and then do a clean install of Karmic on that disk.

My machine has 3 HDDs in it, 2 containing Windows XP stuff, and the 3rd one with Jaunty - obviously dual-boot.

The drive with Jaunty on it is reported in System Monitor as dev/sdc1 and the external drive I wish to copy the entire HDD onto is /dev/sdd1

As I understand it, ```
dd if = /dev/sdc1 of =/dev/sdd1
``` would do this???

Thanks in advance

---

### Post by Mze on 2009-11-12
[How to clone hard drives with Clonezilla]("http://www.tuxradar.com/content/how-clone-hard-drives-clonezilla")

---

### Post by John Bean on 2009-11-12
/dev/sdc1 is a partition on /dev/sdc, so the dd line would copy the partition not the whole disk. If this is what you want to do that's fine, but if you want to "clone" the whole disk to another (whole) disk just drop the partition numbers.

Be careful with the destination though; don't forget that you could write it to a file on another disk rather than to the disk itself.

Edit: and lose the extra spaces around the "=" signs, as in "of=/dev/sdd1" etc.

---

### Post by wojox on 2009-11-12
Yes your dd statement will work.

[http://www.backuphowto.info/linux-backup-hard-disk-clone-dd](http://www.backuphowto.info/linux-backup-hard-disk-clone-dd)

---

### Post by Commander_Keen on 2009-11-12
If you are going to do a clean install anyway, why are you going to clone?
Are you going to leave Windows on, or take it off?
If you are going to make this PC just Ubuntu, then copy the data onto a the external HD and be done with it.

---

### Post by von Stalhein on 2009-11-12
> **Commander_Keen said:**
> If you are going to do a clean install anyway, why are you going to clone?
Are you going to leave Windows on, or take it off?
If you are going to make this PC just Ubuntu, then copy the data onto a the external HD and be done with it.

Other in my family use the the machine, and they are not converted to the Ubuntu advantages yet :-)so it needs to remain dual-boot.

I want to keep all the data presently on this one to gradually customise the new install to be very similar. My upgrade to Karmic had a few insurmountable issue, and it&#347; time to do a clean-up anyway. I want to back the whole thing up and pick and choose what goes back later.

> **wojox said:**
> Yes your dd statement will work.

[http://www.backuphowto.info/linux-backup-hard-disk-clone-dd](http://www.backuphowto.info/linux-backup-hard-disk-clone-dd)

> **John Bean said:**
> /dev/sdc1 is a partition on /dev/sdc, so the dd line would copy the partition not the whole disk. If this is what you want to do that's fine, but if you want to "clone" the whole disk to another (whole) disk just drop the partition numbers.

Be careful with the destination though; don't forget that you could write it to a file on another disk rather than to the disk itself.

Edit: and lose the extra spaces around the "=" signs, as in "of=/dev/sdd1" etc.

Thanks chaps, I&#314;l have a crack.

---

