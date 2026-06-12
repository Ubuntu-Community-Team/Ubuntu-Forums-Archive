---
title: "Ubuntu does not load and cannot mount harddisk"
date: 2011-02-17
forum: General Help
---

### Post by clu3 on 2011-02-17
Hi all,
Please help me rescue some very important data on my hard drive

I'm running ubuntu 10.10 on my Toshiba Satellite L645 laptop. Few hours ago, when my laptop was in screensaver mode, i couldn't login again, it was just blank black screen
So i switch to terminal 1 by pressing Ctrl + Alt + F1 and login from there. Then i restarted by "sudo shutdown -r now". I did this a few times before and it's no problem.

However, this time when the computer boot, I got the errors like : 

---many similar errors like the following line---
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init=bootarg

and redirected to <initramfs> prompt

So i googled and tried the liveCD and try to fix the hard drive with fsck. My partition resides on /dev/sda1 and using ext4

This is what happens:
root@ubuntu:~# fsck -v /dev/sda1
fsck from util-linux-ng 2.17.1
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?


Is my harddrive rescue-able? Thank you


Here is some other extra info if needed

root@ubuntu
 
Disk /dev/sda: 500GB,  200107862016 buytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 106065 * 512 = 8225280 bytes
I/O size (minimum/optimal) : 512 bytes / 512 bytes
Disk identifier: 0x00048969
 
   Device Boot       Start           End           Blocks        Id      System
/dev/sda1   *           1          60037        482241536        83      Linux
/dev/sda2            60037         60802         6141953         5      Extended
/dev/sda5            60037         60802         6141953         5      Linux Sawp / Solaris
 
 
root@ubuntu:~#  sudo cat /etc/mtab
aufs / aufs rw 00
none /proc proc rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mod=0620 00
/dev/sr0 /cdrom iso9660 ro,noatime 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0775 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_isc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ubuntu 0 0
 
 
root@ubuntu:~# sudo blkid
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="70280399-d479-4e53-bd91-345779bfe1bf" TYPE="ext4"
/dev/sda5: UUID="another string here" TYPE="swap"


That's 3 blocks of information i got by following instructions on the IRC channel. I just forgot to paste the first command and now can't remember what it is

---

### Post by TeoBigusGeekus on 2011-02-17
See [this]("http://wwww.ubuntuforums.org/showthread.php?t=1167710") thread.

---

### Post by clu3 on 2011-02-17
> **TeoBigusGeekus said:**
> See [this]("http://wwww.ubuntuforums.org/showthread.php?t=1167710") thread.

@TeoBigusGeekus
Thanks but i already saw that thread before posting this. All the suggestions there didn't work, except for the grub suggestion that i do not have any clues what to do next yet

---

