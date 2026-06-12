---
title: "Weird... Busybox thing"
date: 2010-10-23
forum: General Help
---

### Post by Manifest on 2010-10-23
my ubuntu was working fine until the power lead fell out and when i booted up again it gives me
 ALERT! /dev/disk/by-uuid/LOAD-OF-Numbers does not exist.  Dropping to a shell!
and then something about busybox:(

---

### Post by Jebtrix on 2010-10-23
Since you didn't give any real details on your hard drive (multi drives, multi os) at least run the livecd and gparted to verify drives and partitions are detected/intact.  

There are alot of repairing grub2 related howto's

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by Manifest on 2010-10-24
Ok i have a dual boot of 2 ubuntu's the new one that looks better and the old one.
[IMG]http://i53.tinypic.com/dp8ppl.png[/IMG]

---

### Post by Manifest on 2010-10-24
> **Manifest said:**
> Ok i have a dual boot of 2 ubuntu's the new one that looks better and the old one.
[IMG]http://i53.tinypic.com/dp8ppl.png[/IMG]
bUmP

---

### Post by Rubi1200 on 2010-10-24
Please post the output of the following commands (run them separately):

```
cat /etc/fstab
```

```
sudo blkid
```

---

### Post by Manifest on 2010-10-24
```
root@walrus-laptop:/home/walrus# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=d7a70c81-d0ea-409b-a81e-44d022f821af /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=095e9fde-825c-4ec9-afc7-7e4f7b2f30cb none            swap    sw              0       0
root@walrus-laptop:/home/walrus# 
```

```
root@walrus-laptop:/home/walrus# sudo blkid
/dev/loop0: LABEL="Ubuntu 10.10 i386" TYPE="iso9660" 
/dev/sda1: UUID="3f81086b-f836-40b5-8d08-572923889b41" TYPE="ext4" 
/dev/sda5: UUID="095e9fde-825c-4ec9-afc7-7e4f7b2f30cb" TYPE="swap" 
/dev/sda6: UUID="d7a70c81-d0ea-409b-a81e-44d022f821af" TYPE="ext4" 
/dev/sdb1: UUID="2F95-D06D" TYPE="vfat" 
root@walrus-laptop:/home/walrus# 
```

---

### Post by Rubi1200 on 2010-10-24
What do you have on sda1? A separate home partition or something else?

In any event, it is missing from fstab.

You may want to add it in, save, reboot and see it that fixes the problem.

---

### Post by Manifest on 2010-10-24
how?

---

### Post by Rubi1200 on 2010-10-24
I think you should be able to do it from the LiveCD and running the file manager as root (haven't done this for some time, so a bit rusty).

Open a terminal and type in ```
gksu nautilus
```Navigate to the /etc folder and find the fstab file.

If I understand the screenshot from GParted correctly, sda1 is your separate /home partition?

Add this to the fstab file:

> # /home was on sda1 during installation
UUID=3f81086b-f836-40b5-8d08-572923889b4Then save the file and reboot without the CD.

Hopefully, the problem will be fixed.

If not, there is another way we can do this as well.

Please be careful, with root privileges you can mess things up!

Only edit what I have said and nothing else.

---

