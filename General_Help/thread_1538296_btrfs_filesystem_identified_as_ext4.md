---
title: "btrfs filesystem identified as ext4"
date: 2010-07-24
forum: General Help
---

### Post by Yahoé on 2010-07-24
During the installation of Ubuntu 10.04 the partitioner was wrongfully configured to see a functioning btrfs partition as ext4 (without reformatting it). Thus the installation process got stuck at 5%.

Installer was run again ignoring the btrfs partition.

btrfs-tools was added to the new 10.04, but the btrfs partition is now recognized as ext4 with lost+found folder on it.

Tried to add the btrfs to etc/fstab as btrfs but t won't mount.

Can the partition/filesystem type be changed so that this is actually recognized and mounted as btrfs, hoping my data is still on it somehow?

Regards,

Alain-Olivier
Montréal

---

### Post by Blue Beard on 2010-07-26
> **Yahoé said:**
> During the installation of Ubuntu 10.04 the partitioner was wrongfully configured to see a functioning btrfs partition as ext4 (without reformatting it). Thus the installation process got stuck at 5%.


Even though you specified no format, the system would have mounted the partition as ext4 and tried to write new data to it.

At some point the system could not make sense of the partition and hung.

I do not know of any easy way to salvage the data.

---

### Post by prodigy_ on 2010-07-26
Normally I'd suggest testdisk, but btrfs makes things trickier. I'm not sure if any existing recovery tool will recognize this file system.

---

### Post by Yahoé on 2010-07-26
> **prodigy_ said:**
> Normally I'd suggest testdisk, but btrfs makes things trickier. I'm not sure if any existing recovery tool will recognize this file system.

Indeed it does. I contacted Christophe Grenier the maker of Testdisk. Let's see what comes out of this. Interesting experience on what should not what have happened. Hope others will have ideas.

---

### Post by Blue Beard on 2010-07-26
> **prodigy_ said:**
> Normally I'd suggest testdisk, but btrfs makes things trickier. I'm not sure if any existing recovery tool will recognize this file system.

If the original btrfs was created by conversion from ext3 or ext4, the original ext3 or ext4 version of the file data blocks is preserved.
[https://btrfs.wiki.kernel.org/index.php/Conversion_from_Ext3](https://btrfs.wiki.kernel.org/index.php/Conversion_from_Ext3)

Minus the overwriting.

---

### Post by Yahoé on 2010-07-26
> **Blue Beard said:**
> If the original btrfs was created by conversion from ext3 or ext4, the original ext3 or ext4 version of the file data blocks is preserved.
[https://btrfs.wiki.kernel.org/index.php/Conversion_from_Ext3](https://btrfs.wiki.kernel.org/index.php/Conversion_from_Ext3)

Minus the overwriting.

Yes btrfs-convert had been used for the partition, but I still don't understand, even though yes Ubiquity/partitioner was asked to identify these to btrfs partitions as ext4, how they actually became ext4.
Gparted and mount treat then as ext4 now and though I did not try to write on them I was able to open the lost+found directory. So basically they changed format and that should not have been so.
None of the data that was on them (as btrfs) prior to Ubiquity being run are on them now, that looks awfully like formatting took place or else what!

---

### Post by prodigy_ on 2010-07-26
> **Yahoé said:**
> looks awfully like formatting took place or else what!

I think you should file a bug report. Especially if you're sure you didn't mark the partition for formatting. Most probably btrfs developers would like to hear about the issue. Maybe they'll even suggest you something useful.

---

### Post by Yahoé on 2010-07-26
> **prodigy_ said:**
> I think you should file a bug report. Especially if you're sure you didn't mark the partition for formatting. Most probably btrfs developers would like to hear about the issue. Maybe they'll even suggest you something useful.

Thanks prodigy_ I'm just not sure under what I should file the report, btrfs, Ubiquity?

---

### Post by prodigy_ on 2010-07-27
Probably under btrfs.

---

### Post by Yahoé on 2010-09-16
I contacted Christophe Grenier, the guy behind Testdisk and he answered that he has no idea how btrfs works, let alone fix it.

A bug report was created nearly two months ago forr the Ubiquity team and Chris Mason, but nobody has picked it up or answer any question.

---

