---
title: "Help! Need clone LVM encrypted hard drive to bigger size hard drive!"
date: 2010-12-22
forum: General Help
---

### Post by vcrpcant on 2010-12-22
I need to clone LVM encrypted to a bigger size hard drive.
Need help with MBR, how should I do it?

---

### Post by psusi on 2010-12-22
Partition the new drive as a new LVM PV, and add it to the vg.  Then pvmove the volumes off of the original pv and vgreduce it from the vg.  You might find the system-config-lvm package useful if you don't like the command line.

---

### Post by vcrpcant on 2010-12-22
> **psusi said:**
> Partition the new drive as a new LVM PV, and add it to the vg.  Then pvmove the volumes off of the original pv and vgreduce it from the vg.  You might find the system-config-lvm package useful if you don't like the command line.
Thanks for your reply.
That way I'll be able to connect the second hard drive into another computer and successfully boot?
It is my intention also to keep the first hard drive and continue to use it in the old computer.

---

### Post by vcrpcant on 2010-12-22
I've googled many ways of cloning a hard drive, however, almost always it's mentioned that grub needs to be installed ou recovered from a previous backup; now, I believe Ubuntu 10.04 and 10.10 no longer use grub but grub2 instead. Does this change anything?

---

### Post by psusi on 2010-12-22
Oh, I thought you wanted to just migrate from the old drive to the new one.  If you want to actually duplicate, then yes, you will need to boot from a live cd and use dd to copy the entire drive to the new one, then put it in the new machine and it should boot up, but if the new drive is larger then you will need to extent, which will be a bit tricky with lvm.  There should be no need to reinstall grub.

---

