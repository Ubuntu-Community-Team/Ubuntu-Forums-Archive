---
title: "Uh oh! Hard disk stall"
date: 2011-10-06
forum: General Help
---

### Post by johnuk on 2011-10-06
[This is unbuntu related, but I will explain what's happened to cause the unbuntu problem]

Mum bought a 40" Samsung Smart TV.

I suggested she get a 3TB external drive with it.

I've spent a while trying to get the TV to recognise the drive. I had heard they can't manage partitions of more than a TB or two.

I partitioned the drive in Windows into three single TB blocks, then stuck a few photos on each. I could only see one set of photos on the TV, suggesting it was only recognising one of the partitions; and that was all it was showing in terms of devices.

I went back to try different partitions sizes. 

When I tried deleting partitions, I found I could now only form a partition / partitions up to 2TB, with 800GB unallocated. Even if I delete everything on the drive and every partition, it's still divided for some reason. I can not do anything with the 800GB lump of space. No create new partition, change drive letter or format options. Tried resetting, tried unplugging the drive it's self. No luck.

[the unbuntu bit starts here]

I then figured I might have more luck using gParted.

Plugged the drive into the desktop and tried booting. The boot stalled as it came out of bios.

I unplugged the drive and reset.

Stalled again. Tried unplugged everything and restarting, still stalling.

There's no video signal, nothing happening. If I press the power button, it goes straight off (it usually has a delay).

I stuck the LiveCD in and booted to the OS. 

The OS immediately reported hard disk errors for the internal drive. It says there are significant numbers of bad blocks. 

This is the first time I've ever received this warning.

The drive is still mounted and registering it's partitions and file systems correctly, and marked as bootable. 

But it's not going beyond the bios check.

Any ideas what's going on guys?

Do I need to defag / map the drive?

If anyone has one of the newer samsung smart TV's and can help with that question as well that'd be great!

Cheers!
John

---

### Post by jazzon on 2011-10-06
I dont know about the tv part, but have an external Seagate that hangs (and always) any computer at boot time.  Try Booting, then hot plugging the drive.  That works for mine.

---

### Post by johnuk on 2011-10-06
Yup, I've got the external drive registering when I boot from the LiveCD, but it's the internal drive (with the OS on it) that's reporting the bad sectors and not booting.

---

### Post by johnuk on 2011-10-08
Resolved.

Something was wrong with the MBR.

I ran the boot repair CD and the tool managed to get it going again.

---

### Post by Mark Phelps on 2011-10-08
Then ... please use the Thread Tools to mark this thread as SOLVED.  thanks

---

