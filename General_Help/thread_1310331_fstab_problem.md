---
title: "fstab problem"
date: 2009-11-01
forum: General Help
---

### Post by gft55827 on 2009-11-01
i created a partition (primary) to store my downloads.
formatted it as ext4


sda1 - system
sda2 - swap
sda3 - partition for data

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            9487        9729     1951897+  82  Linux swap / Solaris
/dev/sda3            1217        9486    66428775   83  Linux



Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  4.6G  4.2G  52% /
tmpfs                 495M     0  495M   0% /lib/init/rw
proc                     0     0     0   -  /proc
sysfs                    0     0     0   -  /sys
varrun                495M  228K  494M   1% /var/run
varlock               495M     0  495M   0% /var/lock
udev                  495M  144K  494M   1% /dev
tmpfs                 495M  232K  494M   1% /dev/shm
devpts                   0     0     0   -  /dev/pts
fusectl                  0     0     0   -  /sys/fs/fuse/connections
lrm                   495M  2.5M  492M   1% /lib/modules/2.6.28-16-generic/volatile
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon      0.0K  0.0K  0.0K   -  /home/a/.gvfs
/dev/sda3              63G   13G   51G  20% /data

in order to use partition i have to mount it manually. what should i put to fstab to make os do it for me each time i boot?

/dev/sda3 /data ext4    0 0 0

doesnt work.

---

### Post by fooman on 2009-11-01
did you make the directory first before mounting it?

i would place it in /media if it were me.

to do so,  run in a terminal:

```
sudo mkdir /media/data
```open fstab for editing:

```
 gksudo gedit /etc/fstab
```then add this line to the bottom:

```
 /dev/sda3 /media/data ext4 defaults 0 0
``` save changes and close fstab.

mount:

```
sudo mount -a
```then see if it works.

hope that helps.

---

### Post by gft55827 on 2009-11-01
ok ill try it but tell me why do i have to do it under media?
Of course i made /data dir and as i quote
> in order to use partition i have to mount it manually.

so tell me why /media?

---

### Post by drs305 on 2009-11-01
You don't need to use /media. You can use any mountpoint you wish. There are some old-schoolers who even insist you should not use /media but /mnt, as  /media, was originally designed for removable devices. But in truth it doesn't matter what the mount point is. 

/media is often used because it places the icon on the Desktop automatically, and for examples /media seems to be the most popular mounting point.

The important thing is that the mountpoint exists, and generally, it is best owned by you (sudo chown -R yourusername: /mountpoint.

---

### Post by gft55827 on 2009-11-02
data has sticky bit

it worked, thanks.
can you give me a manual for fstab syntax? i mean other options, what are they for.

---

### Post by HiImTye on 2009-11-02
```
man fstab
```

---

### Post by drs305 on 2009-11-03
> **gft55827 said:**
> data has sticky bit

it worked, thanks.
can you give me a manual for fstab syntax? i mean other options, what are they for.

This is a good thread on fstab:
[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

---

