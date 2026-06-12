---
title: "Accessing Ext4 File System Through Windows"
date: 2010-07-31
forum: General Help
---

### Post by Socialsymbol on 2010-07-31
Windows 7 by default cannot read/mount Ext4 type file systems. I installed Ext2fsd which allows me to mount my linux drive and navigate all the subfolders of my root (/) directory, however when I click on a folder from there (I.E, /home) this is what comes up:

[http://boonce.org/up/9492_Untitled.jpg](http://boonce.org/up/9492_Untitled.jpg)

Any ideas?

---

### Post by clhsharky on 2010-07-31
Socialsymbol

Windows only thinks of itself and the app Ext2fs is not able to read ext4 yet.
Use Ubuntu to copy or move the file you need to a directory that MS can read, NTFS or ext3 with app Ext2fs.

Sharky

---

### Post by zamo2k on 2010-08-24
Hi,

if you just need an utility to access an ext4 partition from Windows, and copy files from it, you can try [Ext2read]("http://ext2read.blogspot.com/")

It does the job for me:
[http://disi.unitn.it/~ferro/index.php/linux/10-read-ext4-partition-with-extents-enabled-from-windows]("http://disi.unitn.it/~ferro/index.php/linux/10-read-ext4-partition-with-extents-enabled-from-windows")

It is not an integration for Windows Explorer, but it's quite handy for me... as I primarily use Linux, and sometimes I need some files in Windows... and I always forget to copy them in the NTFS partition! :p

Hope it helps!
Adamo

---

### Post by zamo2k on 2010-08-24
Hi again,

I've just found also this driver:
[http://www.acc.umu.se/~bosse/]("http://www.acc.umu.se/~bosse/")

The link says
*Ext2fsd-0.48-bb7 Support for ext4 extents and fix for BSOD on Windows 7.*

The official site of Ext2Fsd doesn't say anything about this... maybe the link is of a modified version by the owner of the page...

Maybe you can give it a try!
Let us know!

Bye,
Adamo

---

### Post by echo9 on 2010-10-24
agree with zamo2k ext2read is what you want :popcorn:

---

