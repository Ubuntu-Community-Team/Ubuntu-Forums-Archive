---
title: "Custom 2.6.16 kernel panic on boot"
date: 2006-06-16
forum: General Help
---

### Post by shoffman11 on 2006-06-16
I'm trying to use the new 2.6.16 kernel from kernel.org and the ck12 patchset.  I followed the directions [here]("http://ubuntuforums.org/showthread.php?t=157560").  Everything compiles and installs without errors, but when I boot the kernel, it says> Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)  I tried searching and I found lots of posts with no solutions that work for me.  I have double checked that I have built-in support for my nforce chipset, i have built-in support for ext2 and ext3 (boot and /), and I have built-in support for lvm.  I think the problem is related to lvm.

Here is my /etc/fstab:```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/VolGroup00-LogVol00 /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /boot           ext2    defaults        0       2
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/mapper/VolGroup00-LogVol01 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

/boot/grub/menu.lst:```
title		Ubuntu, kernel 2.6.16-ck12-custom
root		(hd0,2)
kernel		/vmlinuz-2.6.16-ck12-custom root=/dev/mapper/VolGroup00-LogVol00 ro quiet splash
initrd		/initrd.img-2.6.16-ck12-custom
savedefault
boot
```
My .config file is [here]("http://www.bits-dont-byte.com/config-2.6.16-ck12.txt")

I've tried the qmake-dpkg command with and without --initrd.  I've tried compiling modules instead of built-in.  I can't get this to work, and I don't know what else to do.  

Help! Thanks in advance.

P.S.
AMD Athlon64x2 3800+
Asus A8N-SLI premium mobo
2gb corsair xms ddr400 ram
160gb western digital SATA-II hard drive

---

