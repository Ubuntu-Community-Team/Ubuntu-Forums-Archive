---
title: "Can I undelete files from ext4?"
date: 2011-07-14
forum: General Help
---

### Post by Keypel on 2011-07-14
I accidentally deleted everything on a ext4 hard drive. It was deleted not formated. Not a single byte has been written to it since.

Is there a tool to recover the files to another hdd?

---

### Post by dino99 on 2011-07-14
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by jerrrys on 2011-07-14
I have successfully used TestDisk for this

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Keypel on 2011-07-14
Testdisk seems really cool but I don't see a "Linux" partition table type?

```
Please select the partition table type, press Enter when done.
[Intel  ]  Intel/PC partition
[EFI GPT]  EFI GPT partition map (Mac i386, some x86_64...)
[Mac    ]  Apple partition map
[None   ]  Non partitioned media
[Sun    ]  Sun Solaris partition
[XBox   ]  XBox partition
[Return ]  Return to disk selection
```

---

### Post by jerrrys on 2011-07-14
too bad, not going to happen with testdisk.  there are other ways, perhaps you can find one that will work for you...[search here]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=recover+deleted+partition&sa=Search&cof=FORID:9#866").

---

### Post by Keypel on 2011-07-14
> **jerrrys said:**
> too bad, not going to happen with testdisk.  there are other ways, perhaps you can find one that will work for you...[search here]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=recover+deleted+partition&sa=Search&cof=FORID:9#866").


Why can it not happen with testdisk?

I was "testing" testdisk on a 100% good ext4 linux hdd. I just don't see a "Linux" partition table type listed below...

```
Please select the partition table type, press Enter when done.
[Intel  ]  Intel/PC partition
[EFI GPT]  EFI GPT partition map (Mac i386, some x86_64...)
[Mac    ]  Apple partition map
[None   ]  Non partitioned media
[Sun    ]  Sun Solaris partition
[XBox   ]  XBox partition
[Return ]  Return to disk selection
```

But the wiki you listed
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

says it works on ext4 formated partitions. 

> Copy files from deleted FAT, exFAT, NTFS and ext2/ext3/ext4 partitions.

I can not find the "Linux" option for the life of me? All I see is Intel, EFI GPT, Mac, None, Sun, and Xbox.

-

---

### Post by jerrrys on 2011-07-14
because the two times i needed it, it just worked in about 30 seconds.  with you, it did not and i do not know what else can be done from there...goodluck

---

### Post by WorMzy on 2011-07-14
There is no such thing as a Linux partition table type. You're most likely using an Intel partition table, unless you've specifically formatted the disk to use a GPT partition table, or are using a Mac.

Note that "partition table" does not mean "partition". As you can probably guess, partitions sit *within* the partition table.

---

### Post by Keypel on 2011-07-14
> **WorMzy said:**
> There is no such thing as a Linux partition table type. You're most likely using an Intel partition table, unless you've specifically formatted the disk to use a GPT partition table, or are using a Mac.

Note that "partition table" does not mean "partition". As you can probably guess, partitions sit *within* the partition table.

Thanks for the useful reply.

Is there a way to tell if a hdd is mbr or gpt?

---

### Post by srs5694 on 2011-07-14
To elaborate a bit on what WorMzy wrote, a typical hard disk contains several levels of data structures:


[list]
[*]**Partition table** -- This controls the way partitions are defined -- their start points, end points, type code, etc. The most common partition table types are the Master Boot Record (MBR; aka MSDOS partitions, Intel partitions, BIOS partitions; used on most PCs), the Apple Partition Map (APM; used on 680x0- and PowerPC-based Macs), and the GUID partition Table (GPT; used on Intel-based Macs and a few PCs and some other platforms).
[*]**Filesystems** -- These reside inside partitions and provide the means to locate individual files. Examples include ext2/3/4fs, ReiserFS, XFS, JFS, Btrfs, FAT, NTFS, HFS, and HFS+. Any filesystem can exist on a partition defined using any partition table type. Filesystem data structures are much more complex than are partition table data structures.
[*]**File types** -- Files on a filesystem have their own formats, such as ASCII text, JPEGs, MP3s, MS Word files, Linux executable program files, etc. Any file type can reside on any filesystem, although filesystems sometimes impose limits, such as file-size limits, that can be relevant.
[/list]


It's unclear to me precisely what Keypel did, but it sounds like it was deleting files within the ext4 filesystem, in which case the partition table was unaffected. If this is what happened, then TestDisk will be useless, since it's designed to recover a filesystem whose partition table entry has been lost. Instead, [PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) may be useful; it can recover files that have been deleted from healthy filesystems or from filesystems that have been damaged. PhotoRec won't recover everything to exactly its original state, though; it'll take a lot of manual effort to figure out what each and every recovered file actually is. Thus, PhotoRec can be good at recovering personal files, but if you want to recover a bootable Linux system, re-installation is a better choice. (If you need to do both, though, be sure to recover your personal files *before* you re-install! If you do it the other way around, the re-installation may overwrite your personal files, making it impossible to recover them.)

[quote=Keypel]
Is there a way to tell if a hdd is mbr or gpt?
[/quote]

Yes. Many disk utilities will display this information. For instance:

```

$ **sudo parted /dev/sda print**
Model: ATA Hitachi HDP72505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

```

I've omitted additional input; but note that last line, which identifies the partition table type. Many other partitioning tools provide this information in one way or another, but it's highly specific to the particular program.

I don't think this is really very important to your problem, though, unless I've misunderstood what's happened. I recommend you elaborate on what happened:


[list]
[*]How did you accidentally delete everything? Did you use a file manager and drag-and-drop files to the Trash? Did you use "rm -r"? Did you use "mkfs /dev/sda{whatever}"? Did you use "dd if=/dev/zero of=/dev/sda{whatever}"? Did you use a really powerful magnet?
[*]What do you want to recover -- personal files, the OS installation, or both?
[*]What output results when you type "sudo fdisk -lu"? (Please post the results between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags or it will become difficult to interpret.)
[*]What output results when you type "sudo blkid"?

---

### Post by Keypel on 2011-07-14
@srs5694

I was ssh'ing into a samba media server and using mc (midnight commander). I thought I was deleting a tmp folder lol. No recycle bin was setup. I'm pretty sure mc issued the rm -r command.

Everything was deleted from a healthy system. No corruption has taken place and I have not written a single byte to the hdd after the accidental file deletion.

Thanks for the command:

sudo parted /dev/sda print

the partition table is msdos with ext4 filesystem.

I have a mostly current backup of the drive so if recovering is that hard, it's not a big deal.

I guess it sounds like testdisk might not be the best choice? Also, I didn't see a msdos partition table type in testdisk either. Is Intel the same thing?

-

---

### Post by srs5694 on 2011-07-14
The partition table type isn't relevant to your problem, since your partition table hasn't been damaged -- or at least, nothing you've said suggests to me that it has been. This also means that TestDisk will be useless. You've got a straight-up file deletion problem, which means the best recovery method is to restore files from a backup. If you've got important files that were created or changed since your last backup, you could try using PhotoRec to recover them. That can be tedious, but just how tedious depends on details of your system, and whether it's worth the effort depends on the tediousness and the importance of the files to you. The best advice I can give is to try PhotoRec and decide for yourself if it's worth the effort.

In terms of partition table types, "MBR", "MSDOS", "BIOS", and several other terms are synonymous. "MBR" is the current in-vogue term, but several tools use other terms.

---

### Post by Keypel on 2011-07-14
Thanks for the info. I'm not even going to pursue this any further. I'm going to restore my backup and call it one.

---

