---
title: "USB drive identification"
date: 2010-07-28
forum: General Help
---

### Post by paulpepper on 2010-07-28
How can I reliably identify the device used by Ubuntu for a specific external, USB hard disk?

I'm writing a shell script to send data to an external, USB hard disk. Gnome appears to identify the disk as a different devices depending upon the order in which other devices are plugged in. Sometimes the disk is [FONT="Courier New"]/dev/sdc1[/FONT] other times it might be [FONT="Courier New"]/dev/sde1[/FONT], depending upon which other devices are already attached.

Any guidance greatly appreciated.

Paul.

---

### Post by prodigy_ on 2010-07-28
The UUID of an existing partition should always stay the same (unless you explicitly change it with a toll like tune2fs). Use ```
sudo blkid
``` command to see the UUIDs of all partitions. Then you'll be able to mount a partition using its UUID (with **mount -U** command) instead of its device name/number.

---

### Post by oldfred on 2010-07-28
Have you tried giving it a label. I labeled one of my USB flash drives and it auto mounts as the label. You can use labels in fstab so labels are often used.

To add label, you can use gparted, Disk Utility, or command line:
WARNING: mke2fs will reformat your partition and set a label at the same time. This will delete any data on the target partition.

To set a label without reformatting use e2label or tune2fs
e2label <dev> <label>
tune2fs -L <label> <dev>

---

### Post by paulpepper on 2010-07-31
Thanks for the excellent suggestions, guys.

I ended up using [FONT="Courier New"]mount -U[/FONT], after obtaining the drive's UUID with [FONT="Courier New"]blkid[/FONT], as I want to explicitly mount the drive from a script, rather than rely upon Gnome's automounting facilities.

Paul.

---

