---
title: "Primary &amp; Extended Partitions"
date: 2011-06-27
forum: General Help
---

### Post by ssreddy555 on 2011-06-27
What are the advantages (or disadvantages) in partitioning a disc into 4 Primary partitions versus 1 Primary & 3 Extended Partitions?

---

### Post by Wim Sturkenboom on 2011-06-27
Just a small correction

You can not make 3 extended partitions on one disk. Next question :D

You can make 3 primary partitions and one extended partition. The extended one can contain a number of logical partitions.

---

### Post by ratcheer on 2011-06-27
Another idea, which I am currently doing, is to convert to **gpt partitioning**. Then you can have many primary partitions on a disk (128 ?).

Tim

---

### Post by jerrrys on 2011-06-27
got a few hits here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=primary+vs+extended+partition&as_qdr=all&sa=Google+Search&lang=en#971](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=primary+vs+extended+partition&as_qdr=all&sa=Google+Search&lang=en#971)

---

### Post by srs5694 on 2011-06-27
I don't recommend creating four primary partitions on a Master Boot Record (MBR) disk, since that complicates the task of creating additional partitions in the future. At best, you'd need to convert at least one primary to a logical (using [FixParts](http://www.rodsbooks.com/fixparts/) or some other utility) before you could add more. My general advice is to make as many partitions as possible logical partitions. This could even be all of them, although some boot loaders like to see at least one primary partition, so you could maximize your flexibility by making one filesystem partition a primary and everything else a logical partition. If you're multi-booting and more than one OS requires a primary boot partition, of course, you'd need more than one primary partition.

The GUID Partition Table (GPT) is, as ratcheer suggests, another possibility, but that has limitations in terms of bootable OS support. Older OSes and Windows have problems booting from GPT disks on BIOS-based computers. (See [here](http://www.rodsbooks.com/gdisk/booting.html) for details.) For a Linux-only installation, though, or if you want to use the GPT disk as a data disk with another boot disk for Windows Vista or later, GPT provides several advantages over MBR -- over-2TiB disk support, no more primary/extended/logical distinctions, CRCs of important data structures, a backup of important data structures, names for partitions, etc.

---

