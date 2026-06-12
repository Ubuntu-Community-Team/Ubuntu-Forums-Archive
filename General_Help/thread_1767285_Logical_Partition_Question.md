---
title: "Logical Partition Question?"
date: 2011-05-25
forum: General Help
---

### Post by cottfcfan on 2011-05-25
Just bought a new HP unit that came preinstalled with windoze 7.
When I came to partition to install Ubuntu, I noticed that windows takes up 3 of the 4 primary partitions, leaving just 1.
 So I created an extended partition and split into 3 logical ones.
My question is, is running Ubuntu on a logical partition just as safe and stable as running it off a primary one?

---

### Post by srs5694 on 2011-05-25
Essentially, yes.

The one caveat is that the data structures that define logical partitions are more delicate than those that define primary partitions. Logical partitions, unlike primary partitions, are defined in a *linked-list* data structure, in which each partition definition contains a pointer to the next. Thus, /dev/sda5's definition includes a pointer to /dev/sda6, which contains a pointer to /dev/sda7, and so on. If /dev/sda5's definition is damaged, then you could lose /dev/sda6 and all subsequent logical partitions, too.

In practice, this isn't a major issue, particularly if you back up your partition table:

```

sudo sfdisk -d /dev/sda > parts.txt

```

Copy parts.txt to a safe removable medium (a USB flash drive, CD-R disc, floppy disk, or whatever). Then, if your partition table is damaged, you can restore all your partitions:

```

sudo sfdisk -f /dev/sda < parts.txt

```

In terms of use of the filesystems and day-to-day operations, logical partitions are no different from primary partitions as far as Linux is concerned. The partition definitions being in linked lists only affects partitioning software, damage that might be done by misuse of low-level disk utilities, or random disk hardware failures.

---

### Post by satanselbow on 2011-05-25
Yep - and is the recommended (though not essential) way to do it ;)

You can (as I'm sure you know) only have 4 primary partitions on a disk and your extended partition will therefore be your 4th. You can create, pretty much, as many logical partitions as you see fix within the "containing" extended partition.

At a guess W7 is using 2 primary part itself - the 3rd being the factory "recovery" partition ;)

good luck with your install ;)

** Edit - liking the partition table backup trick above :D **

---

### Post by cottfcfan on 2011-05-25
Thanks for your comments guys.
Very helpful.

---

