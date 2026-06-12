---
title: "Ubuntu on Macbook (Recommendations)"
date: 2012-06-11
forum: General Help
---

### Post by Gnome Defender on 2012-06-11
If I install Ubuntu on a Macbook, would I be able to reset the machine to factory settings with the OS it came with in tact (not Ubuntu)?

---

### Post by *^kyfds( on 2012-06-11
if you're new to ubuntu and just want to try it out, you might want to run it in virtualbox, so you don't have any trouble uninstalling it if you don't want it.


Does your macbook have a recovery partition.

---

### Post by markbl on 2012-06-11
> **Gnome Defender said:**
> If I install Ubuntu on a Macbook, would I be able to reset the machine to factory settings with the OS it came with in tact (not Ubuntu)?
I have a current model Macbook Air and yes, you can restore it completely via the internet even if you put a completely new un-partitioned disk in it. Hold command-R at boot and it will boot into the EFI (bios) recovery loader. You can then reinit (repartition) the disk and load it from scratch via the web. You don't need the recovery partition on the disk.

I know this because I stuffed the partitions up just after I got my machine so I used this to completely repartition, reformat, and reload my disk. Took a few hours but got it all back to new.

---

### Post by Gnome Defender on 2012-06-11
> **markbl said:**
> I have a current model Macbook Air and yes, you can restore it completely via the internet even if you put a completely new un-partitioned disk in it. Hold command-R at boot and it will boot into the EFI (bios) recovery loader. You can then reinit (repartition) the disk and load it from scratch via the web. You don't need the recovery partition on the disk.

I know this because I stuffed the partitions up just after I got my machine so I used this to completely repartition, reformat, and reload my disk. Took a few hours but got it all back to new.

Thanks, that's all I wanted to know. :)

---

