---
title: "DF Questions Windows? Linux Partitions"
date: 2009-07-18
forum: General Help
---

### Post by lexusolution on 2009-07-18
I have partitioned my systems with Windows and Ubuntu.  I used df to show disk space

root@ubuntu:~# df -H
Filesystem             Size   Used  Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                        31G   4.4G    25G  16% /
tmpfs                  459M      0   459M   0% /lib/init/rw
varrun                 459M   123k   459M   1% /var/run
varlock                459M      0   459M   0% /var/lock
udev                   459M   148k   459M   1% /dev
tmpfs                  459M   267k   459M   1% /dev/shm
/dev/sda1              121G    42G    79G  35% /host
lrm                    459M   2.3M   457M   1% /lib/modules/2.6.28-13-generic/volatile
root@ubuntu:~# 

I see that /host is where my windows partition resides.  What I wanted to know what are my partitions for my ubuntu installation and my windows installation?  I'm not very comfortable with the file system structure yet and I also would like to know if this df output shows my partitions and current usage.

thank you.

---

### Post by utnubuuser on 2009-07-18
How 'bout> sudo fdisk -lin a terminal, (and that's a small L, not a 1

Windows will probably be ntfs, or Fat, whereas Linux is ext2,3, or 4 and swap.

---

### Post by vinutux on 2009-07-18
> **utnubuuser said:**
> How 'boutin a terminal, (and that's a small L, not a 1

Windows will probably be ntfs, or Fat, whereas Linux is ext2,3, or 4 and swap.

yeh ....sudo fdisk -l give whole info about your system partitions

---

