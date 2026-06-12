---
title: "Totally Boned my Partition Table"
date: 2011-08-10
forum: General Help
---

### Post by robeast on 2011-08-10
In the process of wiping a stubborn USB thumb drive with gparted I accidentally deleted the partition table of my laptop's HDD. The HDD has a partition for Ubuntu, another for Ubuntu Studio and Swap. 

When I boot up a live CD for repair and run testdisk it recognizes only one Linux partition (the first one created) and one Linux Swap if I choose [Intel] partitions. If I choose [EPI GPT] partitions, it recognizes two MS DATA partitions (the two actual Linux partitions) and two Linux Swap partitions and I can't set any as bootable, only primary or deleted. Writing either configuration to MBR results in no boot. 

I backed up everything on the main partition when I realized what I had done, but the other partition could not be mounted? Should I just create images of each partition with testdisk and completely reformat? How boned am I?

---

### Post by oldfred on 2011-08-10
Were your partitions MBR(msdos) or gpt? It makes a big difference. GPT has a backup somewhere as one of its advantages.

MBR has been the standard since the IBM pc. 

Do you have any printout, bootinfo script reports or anything that tells start/end or size of partition? parted rescue can find partitions (may be what testdisk uses), but you have to give it approximate starts & ends within the size it was.

Use parted rescue to restore missing partition
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)

Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by robeast on 2011-08-10
Thanks for the info. I have no idea whether the partitions are MBR or GPT, but I can say that both partitions were created during Ubuntu and Ubuntu Studio install processes, so they should be whatever that creates. testdisk definitely gives me accurate sector sizes of each partition when I choose GPT, so I'll try using those with parted. THANKS!

---

### Post by robeast on 2011-08-10
Bah, humbug! parted rescue wants nothing to do with my partitions! I've been putting in start and end values in MB, is that correct? I've been converting from sectors (testdisk reports partition sizes in sectores) to megabytes by dividing by 2048.

---

### Post by srs5694 on 2011-08-10
The usual way to use TestDisk is to tell it to write your partition table directly. That removes the possibility of human error in copying data. Furthermore, translating from sectors to mebibytes (MiB) will result in rounding errors unless every partition is aligned on MiB boundaries (which is likely if the disk was partitioned with recent enough tools but very unlikely on disks that were partitioned with older tools).

The fact that your computer was unbootable after you recovered partitions using TestDisk in the usual way does *not* mean that TestDisk did anything wrong. After you restore your partitions, you should check the partitions *without* worrying about their bootability -- just try mounting them and accessing their files normally from an emergency boot CD/DVD. If you can do that, then TestDisk recovered the partitions correctly. (Swap space, of course, should be tested by activating it; but swap is easily re-created, so I wouldn't bother testing it.)

A disk's bootability depends on correct partition definitions, at least for the boot partition(s), but it also depends on the presence of appropriate boot code in the MBR (for BIOS-based computers) or files in the EFI System Partition (for (U)EFI-based computers). Thus, particularly for BIOS-based computers, a disk's partitions can be correctly recovered but the computer can be unbootable, and no amount of mucking with partition definitions will change that. To restore a computer in this state to bootability, you must re-install the boot loader.

Concerning MBR vs. GPT partitions, on a Linux-only computer, either will work. The Ubuntu installer generally creates MBR partitions for disks of under 1 TB, but somewhere between 1 TB and 2 TB (I don't know the exact value), it switches to GPT. Given the partitions you describe, you probably had MBR to begin with, but I can't be positive of that. If you go with GPT, you should create a [BIOS Boot Partition,](http://en.wikipedia.org/wiki/BIOS_Boot_partition) which holds boot code that is, on an MBR disk, tucked away in an officially-unused part of the disk.

---

### Post by robeast on 2011-08-10
Thanks for the help! I'm just going to salvage the data from the partitions and start from scratch since I haven't been able to get a valid partition table created with testdisk or parted rescue.

---

### Post by robeast on 2011-08-11
lol, check this out: the Ubuntu 11.04 install process recognized all of the partitions, let me resize one, install Ubuntu on the partition created on the newly freed space, and wrote a proper partition table. I must have just been doing something wrong in testdisk, but if you ever can't get the job done, try what I did, it worked!

---

