---
title: "What it happened with the Kernel?"
date: 2006-06-06
forum: General Help
---

### Post by arsolto on 2006-06-06
Until yesterday the Ubuntu it started without presenting problems and I do not remember to have done nothing that had compromised its health, then, what it happened with the Kernel? I do not obtain to start the Ubuntu!

```
Booting 'Ubuntu, Kernel 2.6.12-10-386' 
Root (hd1,0) 
Filesystem type is ext2fs, partition type 0x83 
Kernel /boot/vmlinuz-2.612-10-386 Root= /dev/sdb1 ro quiet splash 
[linux-bz image, setup=0x1c00, s1ze=0x124d05] initrd / boot/ initrd.img-2.6.12-10-386 
[linux-initrd @ 0xf2d4000, 0x50b5a3bytes] 
save default 
boot 
uncompressing linux... ok, booting the kernel. 
Loading, please wait... 
mount: mounting /dev/sd1 on /root failed: invalid argument 
mount: mounting /root/dev on /dev/.static/dev failed: no such file or directory. 
mount: mounting /dev on /root/dev failed: no such file or directory. 
tareet filesystem doesn't have /sbin/init 

BusyBox v1.00-pre10 (Debian 20040623-ubuntu22) 
Built-in shell (ash) 
Enter 'help' for a list of built-in comands 
/bin/sh: can't access tty; job control turned off
```

I do not have idea of what he can have after occurred disconnect the computer yesterday and to leave the 5.10 Ubutnu or Breeze. Above, we can see the message that I receive from the system during boot, was the only data that I considered important to postar here.

---

### Post by ifokkema on 2006-06-07
Hmm... seems like Linux tries to mount /dev/sd1, fails, and the rest comes down because of that. /dev/sd1 is your root partition, right? Try, from the shell you get, mounting it manually. Something weird in the /etc/fstab maybe???

---

### Post by arsolto on 2006-06-07
For the Explore2fs program I could see the archive _fstab_ and I did not evidence no irregularity. :( 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```
Will be that still valley the penalty to make what you it suggested me? What it can have generated the problem? :???:

---

### Post by ifokkema on 2006-06-08
[QUOTE=arsolto]For the Explore2fs program I could see the archive _fstab_ and I did not evidence no irregularity. :([/QUOTE]
Can you mount your drive from a rescue shell or when booted from the Live CD? Or run fsck over the drive to make sure it's OK?

---

