---
title: "Retrieve Data after Grub Problem"
date: 2010-08-11
forum: General Help
---

### Post by 50cool50 on 2010-08-11
Hi peeps

i have the same problem after installing some stupid updates in ubuntu
i am also green 
i tried all these codes and nothing works ..
i was just wondering is there ay way i can get hold of the files that were on my ubuntu desktop. music and movies and stuff.
is there any way?

thanks guys much appreciate your replies to this

---

### Post by drs305 on 2010-08-11
> **50cool50 said:**
> Hi peeps
<Edit: Reference post [http://ubuntuforums.org/newreply.php?do=newreply&p=9705389](http://ubuntuforums.org/newreply.php?do=newreply&p=9705389) >

i have the same problem after installing some stupid updates in ubuntu
i am also green 
i tried all these codes and nothing works ..
i was just wondering is there ay way i can get hold of the files that were on my ubuntu desktop. music and movies and stuff.
is there any way?

thanks guys much appreciate your replies to this

50cool50,

You should be able to mount your Ubuntu partition from the LiveCD and then retrieve your files.

Boot the LiveCD and open a terminal via Applications > Accessories > Terminal.

Mount your real Ubuntu partition. In the example, it is sda5 (first drive, 5th partition). Change this to point to the correct partition.
```
sudo mount /dev/sd[COLOR="DarkRed"]a5[/COLOR] /mnt
```
You should be able to open a file browser and look at /mnt to see your Ubuntu files. 

Your Desktop files should be located at */mnt/home/<yourusername>/Desktop*


I've moved your post to its own thread since this really isn't about the thread topic and you aren't the OP.

---

### Post by 50cool50 on 2010-08-11
i had vista installed on the p.c.
then i installed ubuntu side by side

what would be the default driver letter for ubuntu usually
i tried a few random variants
nothing worked :(

---

### Post by drs305 on 2010-08-11
> **50cool50 said:**
> i had vista installed on the p.c.
then i installed ubuntu side by side

what would be the default driver letter for ubuntu usually
i tried a few random variants
nothing worked :(

I believe it's usually installed on sda5 in that case, but there is no point in guessing. From the LiveCD terminal, run the following command:
```

sudo fdisk -l  # Note it's a lowercase L, not a numeral

```
You should see an entry "Linux" and another "Linux swap / Solaris". The main linux partition is the one titled "Linux".

---

### Post by 50cool50 on 2010-08-11
i went into gparted utility programme and it shows my hard drive as being called sda1 
i ran the code in terminal again with sda1 and it said "already mounted"

i cant find my files in the file browser location that you suggested ](*,)

---

### Post by drs305 on 2010-08-11
> **50cool50 said:**
> i went into gparted utility programme and it shows my hard drive as being called sda1 
i ran the code in terminal again with sda1 and it said "already mounted"

i cant find my files in the file browser location that you suggested ](*,)

The *drive* would be *sda*; only partitions have the numeral attached.

If your real Linux partition is already mounted, you can find it by running the "mount" command. It will list all the partitions currently mounted and you should be able to find it in the results.

You should also be able to open Nautilus and look in the left pane to find the partition which contains your data, since it is already mounted.

---

### Post by 50cool50 on 2010-08-11
> **drs305 said:**
> The *drive* would be *sda*; only partitions have the numeral attached.

You should also be able to open Nautilus and look in the left pane to find the partition which contains your data, since it is already mounted.

how do i run nautilus?

---

### Post by 50cool50 on 2010-08-11
i ran the mount command in terminal and it came up with this:

ubuntu@ubuntu:~$ sudo mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/TIME MACHINE HD type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /mnt type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
ubuntu@ubuntu:~$ 



any ideas??

---

### Post by 50cool50 on 2010-08-11
the time machine is my plug in usb hard drive

---

### Post by 50cool50 on 2010-08-11
have i lost my files then?
oh dear..so sad..

---

### Post by 50cool50 on 2010-08-11
> **drs305 said:**
> I believe it's usually installed on sda5 in that case, but there is no point in guessing. From the LiveCD terminal, run the following command:
```

sudo fdisk -l  # Note it's a lowercase L, not a numeral

```You should see an entry "Linux" and another "Linux swap / Solaris". The main linux partition is the one titled "Linux".

i ran the command, i dont see anything labelled linux. Heres what it came up with:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS
ubuntu@ubuntu:~$

---

