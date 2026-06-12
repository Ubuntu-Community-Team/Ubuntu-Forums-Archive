---
title: "LiLo Not booting"
date: 2010-10-23
forum: General Help
---

### Post by aidenscool09 on 2010-10-23
Ok, so yesterday I installed LiLo to my HDD and then I made my lilo.conf. It contained this:
```

boot=/dev/sda
map=/boot/map
install=/boot/boot.b
compact
prompt
timeout=50
image=/boot/vmlinuz-2.6.35.7
	label=linux
	root=/dev/sda1
	read-only

```
I just compiled the latest kernel.org stable kernel (2.6.35.7) and then I ran ```
liloconfig
``` and then ```
lilo
```.
If this helps this is my /etc/fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=fdaf6850-960d-484a-83f0-78f8781a98d5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=765304f1-64e5-4d67-abb2-b00825dc0166 none            swap    sw              0       0
/dev/sdb1	/media/storage	ext4	defaults	0	0

```
the /dev/sdb1 is my second hard drive by the way.

---

### Post by aidenscool09 on 2010-10-23
B u m p

---

### Post by aidenscool09 on 2010-10-23
Bump! Please help, this is urgent!

---

### Post by oldfred on 2010-10-23
I thought lilo was not updated to work with ext4 partitions. What is wrong with grub2?

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
or
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

