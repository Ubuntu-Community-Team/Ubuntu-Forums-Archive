---
title: "HELP! Ubuntu installed on the same partition as Windows 7?"
date: 2011-04-17
forum: General Help
---

### Post by overtheedge86 on 2011-04-17
I used windows computer manager to shrink the current partition and installed ubuntu on the freespace. I thought this would create a partition but i do not see a new partition with gparted or the windows computer manager. I believe ubuntu installed on the windows partition. Either OS will boot and run just fine but i think the install went wrong.

---

### Post by skynet2060 on 2011-04-17
Perhaps, you did not explicitly create a new partition, you just reduced how much of the current partition Windows was using. 

When you installed ubuntu, you put in on the same partition as Windows. gparted can't see the new partition because it is not there. Neither can windows, because it can not read linux file systems.

---

### Post by themusicalduck on 2011-04-17
Did you install Ubuntu from within Windows? or did you boot your computer from the Ubuntu CD and install it that way?

If you did it the first way, then it will have installed Ubuntu on the Windows partition. This creates a file on the Windows partition that acts like a virtual partition with a linux filesystem on it.

If you want to install Ubuntu to its own partition, then the best way is to boot from the CD and tell the installer to install Ubuntu side by side with Windows. Then the installer will automatically resize the Windows partition and create a new one for Ubuntu.

---

### Post by Mark Phelps on 2011-04-18
> **themusicalduck said:**
> If you want to install Ubuntu to its own partition, then the best way is to boot from the CD and tell the installer to install Ubuntu side by side with Windows. Then the installer will automatically resize the Windows partition and create a new one for Ubuntu.
\
No, No, NO.  This is the BEST way to risk corrupting the current MS Windows install and rendering it unbootable!

The BEST way to do this is to use the Windows Disk Management utility to shrink the OS partition, leaving room for Ubuntu, and then reboot into Windows a couple of times to resynch the filesystem.

---

### Post by themusicalduck on 2011-04-18
> **Mark Phelps said:**
> \
No, No, NO.  This is the BEST way to risk corrupting the current MS Windows install and rendering it unbootable!

The BEST way to do this is to use the Windows Disk Management utility to shrink the OS partition, leaving room for Ubuntu, and then reboot into Windows a couple of times to resynch the filesystem.

Fair enough. Why do Canonical include such a feature if it risks rendering Windows unbootable?

Normally I'd recommend that method because it's so easy and automatic for users.

---

### Post by Mark Phelps on 2011-04-18
> **themusicalduck said:**
> Fair enough. Why do Canonical include such a feature if it risks rendering Windows unbootable?

Because they don't actually CARE if folks trash their Windows install in the process??  Who knows!

These are the same folks that removed "Use largest free space" option from their installer so that now, folks must use Manual Partitioning, and if they make a simple mistake -- they completely erase their Windows install by accident!

If you want to know why they have done such unbelievably stupid things, you have to ask them.

---

