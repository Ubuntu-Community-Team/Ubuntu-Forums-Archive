---
title: "Confusing Disk Image"
date: 2010-02-03
forum: General Help
---

### Post by deamon_knight on 2010-02-03
I have a disk image ending in .imz , which boots a light diagnostic utility. I'm trying to modify the content of this image. This is a compressed floppy disk image. I can uncompress it and the mount the resulting .IMA file with the loop device. However, the only file on this disk is a .dat file. Any suggestions on how to open this file. I know it must contain a bootable disk image, as I can boot the original .imz file. However, I don't know anything more about this .dat file. I suspect its a ext2/3 image but trying:
 *sudo mount -t ext3 -o loop ~/ultrqax/uxboot.dat /media/test/* does not work, I get:
[I]mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/I]

same with trying to specify ext2.

 Any suggestions?

---

