---
title: "NTFS read/write advice please"
date: 2006-06-15
forum: General Help
---

### Post by xenomorph99 on 2006-06-15
Hi,

The NTFS howto suggests that this is risky and experimental although it's "quite safe unless there is a bug", pardon my paraphrasing. 

In effect, that tells me nothing. 

So, just how risky and experimental is it? Do tales of woe clearly outnumber those of joy? If it goes wrong, what does it generally do? Trash the entire disk or just the partition you were monkeying with?

When it does trash something, what is the failure mode? Is it easily recoverable? How long is a piece of string?

Ta,
Xeno

---

### Post by eth on 2006-06-15
Up till now the NTFS writing support is experimental, and, following the 2.6.15 menuconfig help, it is restricted to substitution of preexistent files with others of SAME name and SAME lenght, in bytes...the point, correct me if I am wrong, is that linux can actually write on a partition with NTFS but he cannot change the pointer in the partition table to the file and rebuild a solid structure for it. So he just can "overwrite" lines already written and leave the pointer believing nothing happened

---

### Post by sugonaut on 2006-06-15
With 5 cups of Ubuntu under your belt, why are you asking about NTFS support?  You should have deleted your windows partition by now :-)

Okay...seriously...go with a FAT32 partition.  It's works well enough to share files across your dual boot.

---

### Post by veratyr on 2006-06-15
I heard Xandros 4 was going to have NTFS read/write support. Any idea of the state of this or if it will make it into other distros?

---

### Post by jodar on 2006-06-15
Is there a free way to convert a partition from NTFS to FAT32 without losing data?

I have a dual boot on my laptop with all of my windows being contained on one partition.  Curious if I can correct this with something like gparted or if I just need to file this away as a "next time I install windows use fat32 incase I dual boot".

---

### Post by xenomorph99 on 2006-06-16
[QUOTE=sugonaut]With 5 cups of Ubuntu under your belt, why are you asking about NTFS support?  You should have deleted your windows partition by now :-)

Okay...seriously...go with a FAT32 partition.  It's works well enough to share files across your dual boot.[/QUOTE]

I do use a FAT32 partition to share files; trouble is, I'd like to be able to r/w my other partitions directly without having to ponce about (well, more precisely, I made the mistake of not making the FAT32 partition big enough to hold a ripped DVD image). 

I suppose I could repartition yet again but my drive has been repartitioned that many times for Linux that I fear it will wear out.

Ta,
Xeno

---

### Post by lamego on 2006-06-16
There is captive which is an wrapper around the windows native ntfs driver so it should be stable:

[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

---

### Post by cotcot on 2006-06-16
Consider ext2 or ext3 as filesystem for shared files. It has not the disadvantage of a 4 GB filelimit as FAT32 has. OK 4 GB is a big file, but when you make videos from a camcorder or backup images it is not so big any more. Ext2/3 is accessible from XP by installing a simple and open source driver : [http://fs-driver.org/]("http://fs-driver.org/")

---

### Post by Anduu on 2006-06-16
Well I haven't had any troubles with read/write to ntfs and I have been using it for a couple of months now.

I suppose the worst thing it could do is hose your ntfs partition but I have already backed up all my important Windows stuff so if it does it does :razz:

---

