---
title: "Issues creating Windows 7 Repair Disc in Linux"
date: 2010-03-14
forum: General Help
---

### Post by Derek.Gildea on 2010-03-14
I used third-party windows software to extend my primary windows 7 partition. Halfway through the process the software crashed and now Windows no longer loads.

I'm trying to create a Windows 7 Repair CD in Linux, but keep running up against a wall. I use Unetbootin to create the Windows 7 Repair CD, but am unable to boot off the resulting USB key in GRUB. I suspect it is because Unetbootin is made only for Linux software?

Is there another way to create a Windows 7 Repair CD in Linux? What other software can create a USB with an image?

---

### Post by wilee-nilee on 2010-03-14
What do the W7 partitions look like from gparted? you might give us a screenshot.

I think you will have to get a usb cd burner to use the recovery disc.

---

### Post by Derek.Gildea on 2010-03-14
Oof - that's the issue. Currently gparted shows the entire drive as unallocated because a) the partition table was changed and b) (I assume) because the partition on which I installed windows is a little screwy due to crashed partitioner.

And, as luck would have it, I've discovered that the Windows 7 System Repair disk has to be made by the user, and that it's illegal to download it.

Think testdisk will help me out here?

---

### Post by wilee-nilee on 2010-03-14
> **Derek.Gildea said:**
> Oof - that's the issue. Currently gparted shows the entire drive as unallocated because a) the partition table was changed and b) (I assume) because the partition on which I installed windows is a little screwy due to crashed partitioner.

And, as luck would have it, I've discovered that the Windows 7 System Repair disk has to be made by the user, and that it's illegal to download it.

Think testdisk will help me out here?

I have never had to due any recovery so I can't help here.

What I wonder is if there is a recovery partition, it may be that you can recover stuff and then use the recovery to set it back to the purchase OS.

Here is a recovery ISO this is for a less damaged system then yours, and requires a basically set up system. It may have the option of running recovery though if you have a recovery partition.

I would get a install ISO or DVD in the end no matter what.

---

### Post by Mark Phelps on 2010-03-15
> **Derek.Gildea said:**
> ... And, as luck would have it, I've discovered that the Windows 7 System Repair disk has to be made by the user, and that it's illegal to download it.

Now THAT's certainly not true! You simply can't use it to install Win7 (it doesn't have the necessary files), so I have no idea why anyone would say it's illegal to have such a disk.

Go to the NeoSmart Technology forums and download the appropriate (32-bit or 64-bit) Win7 repair CD ISO file, burn it to CD, and you have a Win7 Repair CD.

---

