---
title: "NTFS Case Insensitive Needed (or any FS case insensitive)"
date: 2010-01-06
forum: General Help
---

### Post by tdiaz on 2010-01-06
I'm using NetATalk with Apple II's and older Macs, and am in need of a case-insensitive solution. I picked NTFS because .. based on my experience with Windows/Mac/Samba/external drives .. that it as case insensitive.

But not in Linux. 

The problem is related to scripts and applications that are written with case preservation in mind, but not case sensitivity. 

I'll presume this is a product of NTFS-3G. Is there a way to do it otherwise?

---

### Post by domatic on 2010-01-07
> **tdiaz said:**
> I'm using NetATalk with Apple II's and older Macs, and am in need of a case-insensitive solution. I picked NTFS because .. based on my experience with Windows/Mac/Samba/external drives .. that it as case insensitive.

But not in Linux. 

The problem is related to scripts and applications that are written with case preservation in mind, but not case sensitivity. 

I'll presume this is a product of NTFS-3G. Is there a way to do it otherwise?

AFAIK only JFS has both a case-preserving option and a full set of tools to make and fsck the filesystems.  You have to specify that the JFS filesystem is case-preserving at the time of creation with the -O (uppercase "O") option.  If you want to go this route, you'll have to backup your netatalk share and put the files back after doing this as you will be reformatting a disk partition:

apt-get install jfsutils

mkfs.jfs -O /dev/sda2 (or whatever)

Mount and share that with netatalk and it will pretty much behave as you are needing it to.

---

### Post by tdiaz on 2010-01-07
Hmmm.. JFS.. 

So it does have case preservation and insensitivity options. 

I've read more "crud" about JFS than good, but .. nothing as or recent dates, mostly all 2004-2006 era.

.. thanks for the input. I'll have to drop a partition and try it at least.

Basically what I've run into is an existing source code base and it's associated scripts. They seem to be written where some times FileNames are CamelCase, othertimes they are lowercase and even others they are UPPERCASE or mixed variations for the same files. I'm trying to set this codebase up on a server. 

Otherwise finding nearly 3,000 file names in various scripts in at least 500 directories is.. nuts. 

If it were a case of starting from scratch, the case sensitivity wouldn't be much of an issue.  Just follow ones own guidelines and you're all good.

---

