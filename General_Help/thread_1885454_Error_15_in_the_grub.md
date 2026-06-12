---
title: "Error 15 in the grub"
date: 2011-11-23
forum: General Help
---

### Post by adbforum on 2011-11-23
I installed new ubuntu and after the reboot , error 15 is shown, how to fix this ?
what do I need to change ?
I was win user so I am new of linux,tnx

this is the output of my console



[23:51:50] delcopc@delcopc:~ $ sudo fdisk -l | grep -i linux
/dev/sdb1   *           1       38184   306709504   83  Linux
/dev/sdb5           38184       38914     5859328   82  Linux swap / Solaris
[00:19:26] delcopc@delcopc:~ $ sudo updatedb
[00:20:18] delcopc@delcopc:~ $ locate menu.lst
/usr/share/doc/memtest86+/examples/grub-menu.lst
[00:20:49] delcopc@delcopc:~ $ cat /usr/share/doc/memtest86+/examples/grub-menu.lst


# sample /boot/grub/menu.lst entry for memtest86
#
# This example assumes the contents of /boot is on the root partition.
# If your /boot is on its own partition, remove /boot from the 'kernel' line.

title  memtest86+
root   (hd0,0)
kernel /boot/memtest86+.bin

title  memtest86+ (serial console 115200)
root   (hd0,0)
kernel /boot/memtest86+.bin console=ttyS0,115200n8

---

### Post by drs305 on 2011-11-23
The error number is associated with booting using Grub legacy. But a search only displays one menu.lst file which is not in the normal location. You should be booting Grub 2, but I don't know how you are ending up with a Grub legacy error message. If you run the following command, you can tell which version of Grub you are using:
```
grub-install -v
```

If it shows Grub 0.97, I'd strongly recommend you upgrade to Grub 2. There is a bit of a learning curve but Grub 2 has a lot of advantages. The Grub 2 package is called 'grub-pc'.

Since you probably aren't able to boot with a Grub 15 error message, I'd use the Ubuntu LiveCD to install Grub 2 via the 'chroot' method described in the 'Chroot' link in my signature line. If you have questions about the procedure, just ask.

I normally try to answer questions more directly rather than suggest alternative options, but I've forgotten most of what I knew about Grub legacy.

---

