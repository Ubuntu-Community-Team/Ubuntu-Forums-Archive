---
title: "Help! GRUB error 17 on Jaunty"
date: 2009-09-04
forum: General Help
---

### Post by MKelly on 2009-09-04
I've done a search but don't know enough to risk trying to solve on my own.
This is what I've found so far:

ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 20.0 GB, 20003880960 bytes
15 heads, 63 sectors/track, 41344 cylinders
Units = cylinders of 945 * 512 = 483840 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       40284    19034158+  83  Linux
/dev/sda2           40285       41344      500850    f  W95 Ext'd (LBA)
/dev/sda5           40285   



OK, spent hours reading the forums and after running efsck, it corrected a LOT of errors.  Now I no longer get the dreaded GRUB error 17 message; it hangs a bit further in the boot process- something about missing sbin/init, then kernel panic.  However, when I boot from the CD, I can mount the hard drive and see my files. I checked, and there is an init file in sbin. So, what do I need to do to fix this now?

And now I get this:
ubuntu@ubuntu:~$ sudo fdisk -l 
Disk /dev/sda: 20.0 GB, 20003880960 bytes
15 heads, 63 sectors/track, 41344 cylinders
Units = cylinders of 945 * 512 = 483840 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       40284    19034158+  83  Linux
/dev/sda2           40285       41344      500850    f  W95 Ext'd (LBA)
/dev/sda5           40285       41344      500818+  82  Linux swap / Solaris

/boot/grub/menu.lst copied below:

title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-6-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-6-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro quiet splash 
initrd		/boot/initrd.img-2.6.28-6-386

title		Ubuntu 9.04, kernel 2.6.28-6-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-6-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro  single
initrd		/boot/initrd.img-2.6.28-6-386

title		Ubuntu 9.04, kernel 2.6.25-2-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.25-2-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro quiet splash 
initrd		/boot/initrd.img-2.6.25-2-386

title		Ubuntu 9.04, kernel 2.6.25-2-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.25-2-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro  single
initrd		/boot/initrd.img-2.6.25-2-386

title		Ubuntu 9.04, kernel 2.6.24-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-386

title		Ubuntu 9.04, kernel 2.6.24-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro  single
initrd		/boot/initrd.img-2.6.24-23-386

title		Ubuntu 9.04, kernel 2.6.22-16-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-16-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro quiet splash 
initrd		/boot/initrd.img-2.6.22-16-386

title		Ubuntu 9.04, kernel 2.6.22-16-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-16-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro  single
initrd		/boot/initrd.img-2.6.22-16-386

title		Ubuntu 9.04, kernel 2.6.17-12-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro quiet splash 
initrd		/boot/initrd.img-2.6.17-12-386

title		Ubuntu 9.04, kernel 2.6.17-12-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro  single
initrd		/boot/initrd.img-2.6.17-12-386

title		Ubuntu 9.04, kernel 2.6.17-11-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro quiet splash 
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu 9.04, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro  single
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu 9.04, kernel 2.6.15-28-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro quiet splash 
initrd		/boot/initrd.img-2.6.15-28-386

title		Ubuntu 9.04, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro  single
initrd		/boot/initrd.img-2.6.15-28-386

title		Ubuntu 9.04, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-386

title		Ubuntu 9.04, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro  single
initrd		/boot/initrd.img-2.6.15-27-386

title		Ubuntu 9.04, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro quiet splash 
initrd		/boot/initrd.img-2.6.15-26-386

title		Ubuntu 9.04, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro  single
initrd		/boot/initrd.img-2.6.15-26-386

title		Ubuntu 9.04, kernel 2.6.12-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro quiet splash 
initrd		/boot/initrd.img-2.6.12-10-386

title		Ubuntu 9.04, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro  single
initrd		/boot/initrd.img-2.6.12-10-386

title		Ubuntu 9.04, kernel 2.6.12-9-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro quiet splash 
initrd		/boot/initrd.img-2.6.12-9-386

title		Ubuntu 9.04, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro  single
initrd		/boot/initrd.img-2.6.12-9-386

title		Ubuntu 9.04, kernel 2.6.10-5-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro quiet splash 
initrd		/boot/initrd.img-2.6.10-5-386

title		Ubuntu 9.04, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro  single
initrd		/boot/initrd.img-2.6.10-5-386

title		Ubuntu 9.04, kernel 2.6.8.1-5-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-5-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro quiet splash 
initrd		/boot/initrd.img-2.6.8.1-5-386

title		Ubuntu 9.04, kernel 2.6.8.1-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-5-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro  single
initrd		/boot/initrd.img-2.6.8.1-5-386

title		Ubuntu 9.04, kernel 2.6.8.1-3-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro quiet splash 
initrd		/boot/initrd.img-2.6.8.1-3-386

title		Ubuntu 9.04, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=UUID=6d21c617-c26c-4949-8ee2-f8ae775caaaf ro  single
initrd		/boot/initrd.img-2.6.8.1-3-386

title		Ubuntu 9.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

---

