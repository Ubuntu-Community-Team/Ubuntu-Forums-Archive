---
title: "Help! Problem with paritions!"
date: 2010-12-24
forum: General Help
---

### Post by The Elite Noob on 2010-12-24
Hiya! I have a question, i have two hard drives, a 500 gb one, and a 40 gb one.
On the 40 gb one, with 4 partitons,

[LIST=1]
[*]One 1.5 gb swap space
[*]3 gb /tmp
[*]15 gb partiton for /boot
[*]and a 20 gb for /root or /
[/LIST]
Now, i need to increase my /root partiton into my /home one, so my root can be a 50 gb partiton. 20 gb from the 40 gb hd, and a 30 gb from the 500 gb hard drive.
now how can i do this? help please!

---

### Post by Bitrate on 2010-12-24
sudo apt-get install gparted

---

### Post by JC Cheloven on 2010-12-24
So, your /home partition currently stuffs tour 500gb HD, right?
And you want to increase your root partition taking space from that other disk. Thus your root would result splitted in two physical disks (!). 

I'm not sure if that's feasible. It isn't to my humble knowlegde, though. I'd say you'll need to reinstall with a better planned partition scheme.

BTW, your complicated setup caught my attention. 15 Gb for /boot: why that much? And that many partitions... is it a server? Anyway, best of luck. Perhaps someone else has a more clever idea.

EDIT: perhaps if you post the output of the following comands at terminal, someone can gain a better understanding of your setup:
```
sudo fdisk -l
``` ```
sudo mount
```

---

### Post by The Elite Noob on 2010-12-25
> **JC Cheloven said:**
> So, your /home partition currently stuffs tour 500gb HD, right?
And you want to increase your root partition taking space from that other disk. Thus your root would result splitted in two physical disks (!). 

I'm not sure if that's feasible. It isn't to my humble knowlegde, though. I'd say you'll need to reinstall with a better planned partition scheme.

BTW, your complicated setup caught my attention. 15 Gb for /boot: why that much? And that many partitions... is it a server? Anyway, best of luck. Perhaps someone else has a more clever idea.

EDIT: perhaps if you post the output of the following comands at terminal, someone can gain a better understanding of your setup:
```
sudo fdisk -l
``` ```
sudo mount
```

I thought i would need that for boot, for the kernel, looks like i was mistaken.

so here is the output of
```

sudo fdisk -l 
```
```


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bede6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384512   83  Linux

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00010638

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         426     3417088   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2             426        4866    35662849    5  Extended
/dev/sdb5             608        2432    14647296   83  Linux
/dev/sdb6            2432        4866    19550208   83  Linux

Disk /dev/sdc: 4040 MB, 4040748544 bytes
125 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000e09b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1018     3944719    b  W95 FAT32

```

and output of 
```

sudo mount 

```
```

/dev/sdb6 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
/dev/sda1 on /home type ext4 (rw,commit=0)
/dev/sdb1 on /tmp type ext4 (rw,commit=0)
/dev/sdb5 on /boot type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/theelitenoob/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=theelitenoob)
/dev/sdc1 on /media/NOOB type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

```

---

### Post by JC Cheloven on 2010-12-25
Mmmm... first of all, you think you have a swap space, but you haven't any. Swap partition should be listed by fdisk -l. It is generally advised to have a swap partition as big as your ram. Not that serious though (it will be seldom used; some people thinks it's actually a waste of disk space).

As to the rest, your former explanation was quite accurate. 
Again, I may be wrong, but I think *what you intend to do is not feasible*, for the reason mentioned in my previous post. 

So, some alternate advice: some 300Mb should be largely enough for /boot. You could take almost the entire 15Gb (14.7) to expand the root. You would end up with a almost a 35Gb for root. ¿Should that be convenient?
[INDENT]in order to do so, start from live, fire up gparted, shrink sdb5 to ~300Mb (apply changes), expand sdb6 to fill the recently freed space (apply changes) [/INDENT]
That may take a while, and is somehow prone to errors in my experience, but it should work. BTW I assume that your sensible data is in sda, thus safe regarding these operations.

If you finally consider reinstalling, and don't have any serious reason to do otherwise, I'd suggest to keep your /home in sda1 (that's good habits), but no separate partitions for /boot and /temp. Rather root (/) in a new sdb1 resized to say 38 Gb, which will include /boot & /temp as folders, and a new sdb2 of about 2Gb for swap. Both may be primary, no problem. If unsure, you can post a screenshot of gparted (on your sdb disk) before doing permanent changes.

Cheers

---

### Post by okkadiroglu on 2010-12-26
Hi,

I am having a similar problem too. I think after the most recent update this happened. In my case I would like to increase disk space /dev/sda1 for the /. How can I do it?

Many thanks

results for fdisk -l and mount is given below.


oyo@oyo-desktop:~$ sudo fdisk -l

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x97669817

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c2869

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         851     6835626   83  Linux
/dev/sda2             852       14593   110382615    5  Extended
/dev/sda5             852        1419     4562428+  82  Linux swap / Solaris
/dev/sda6            1420       14593   105820123+  83  Linux
oyo@oyo-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
/dev/sdb1 on /home type ext3 (rw)
/dev/sda6 on /usr type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/oyo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=oyo)

---

### Post by okkadiroglu on 2010-12-26
Hi,

Additional information from GParted.

/dev/sda1          ext3          /          6.53GB          6.45GB          69.72MB          boot
/dev/sda2          extended            105.27GB

/dev/sda5           linux-swap             4.35GB
/dev/sda6           ext3       /usr      100.92GB      10.38GB       90.52GB

---

### Post by The Elite Noob on 2010-12-26
@JC Cheloven
Thanks man! I'll do that now!
Really appreciate it!

> **okkadiroglu said:**
> Hi,

Additional information from GParted.

/dev/sda1          ext3          /          6.53GB          6.45GB          69.72MB          boot
/dev/sda2          extended            105.27GB

/dev/sda5           linux-swap             4.35GB
/dev/sda6           ext3       /usr      100.92GB      10.38GB       90.52GB

Make your own thread mate...
these are my problems...

---

### Post by JC Cheloven on 2010-12-29
> **The Elite Noob said:**
> @JC Cheloven
Thanks man! I'll do that now!
Really appreciate it!


You're welcome. Did you finally found your way?

---

### Post by The Elite Noob on 2010-12-31
> **JC Cheloven said:**
> You're welcome. Did you finally found your way?

Yep, i first noted all the packages i downloaded, things i had installed,
then reinstalled ubuntu, set / on my 40 gb partiton, and restored my software.

---

