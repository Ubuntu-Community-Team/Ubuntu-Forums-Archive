---
title: "Ext2Fsd Read support with Extents, Win7"
date: 2011-01-12
forum: General Help
---

### Post by cragdor on 2011-01-12
Hi All,
I recently had to reinstall windows a spare partition on my computer due to work commitments.
Anyways a long story short, most of my important data is on an Ext4 partition normally mounted to ‘/home’.
After searching around for a while I discovered that Ext2Fsd, would not by default read Ext4 with the Extents bit. However it seems there are a few developers out there that have been working on the problem and there is a solution that is not yet released. Thanks to the ‘Academic Computer Club Umeå University’.
** This is not release software! **

1)	Go to: [http://sourceforge.net/projects/ext2fsd/files/](http://sourceforge.net/projects/ext2fsd/files/) install version 0.48. 
2)	When it completed installation do not load the disk manager.
3)	Go to: [http://www.acc.umu.se/~bosse/](http://www.acc.umu.se/~bosse/) > click link Ext2fsd-0.48-bb8 > save it.
4)	Open the zip file.
5)	Read the README *64bit needs driver sign check disabled!*
6)	Open fre, select your architecture
a.	32bit > ‘i386’
b.	64bit > ‘amd64’
7)	Copy the sys file to /windows/system32/drivers
8)	You will be prompted to replace an existing file, you will them be prompted for admin rights.
9)	Restart!
a.	64 bit users, This driver is not signed so on 64-bit systems you must press F8 and select: "Disable enforce driver signing" at boot.
10)	Load ‘Ext2 Volume manager’, assign drive letters, restart as necessary.

**Please note 64 bit users will always need to do 9a, I’m not sure if there is a way to permanently disable it, but I suspect it will not be an issue when a official release is made. **

Regards,

Craig Thomas

---

