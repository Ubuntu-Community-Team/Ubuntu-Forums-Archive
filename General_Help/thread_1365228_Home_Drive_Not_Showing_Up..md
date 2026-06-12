---
title: "Home Drive Not Showing Up."
date: 2009-12-27
forum: General Help
---

### Post by Sef on 2009-12-27
[s]My home parition is showing only 105 GB instead of 260 or so.   I know this is not a new problem, but I have been unable to find a thread on this problem here so far.   So if someone has an answer or a link to a thread, I would most appreciate it.[/s]

My home drive is not showing up under either Computers or Places.  Why?

---

### Post by hwttdz on 2009-12-27
Can you post the output of 

sudo fdisk -l

Where is it showing these sizes?

---

### Post by Sef on 2009-12-27
Output of fdisk -l: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e929b2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12779   102647286    7  HPFS/NTFS
/dev/sda2   *       12780       14691    15358140   83  Linux
/dev/sda3           14692       60801   370378575    5  Extended
/dev/sda5           14692       16603    15358108+  83  Linux
/dev/sda6           16604       16730     1020096   82  Linux swap / Solaris
/dev/sda7           16731       60801   354000276   83  Linux

The partition is /dev/sda 7.

---

### Post by Sef on 2009-12-27
Realized have erred, so changed title.  105 is my Windows partition.  However, my home drive is not showing up under Places nor Computer.   That is 362 gb.

---

### Post by oldfred on 2009-12-27
Is it in your fstab?  and if you do a mount -a do you get any errors.

Also does df -h show it mounted and size?

---

### Post by Sef on 2009-12-27
dh -f: 

> sef@joker:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              15G  3.1G   11G  23% /
udev                  2.0G  324K  2.0G   1% /dev
none                  2.0G  504K  2.0G   1% /dev/shm
none                  2.0G   84K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda7             333G  1.3G  315G   1% /home
sef@joker:~$ 


mount -a:

> sef@joker:~$ sudo mount -a
[sudo] password for sef: 
sef@joker:~$ 


fstab:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=77bcdce5-a2ac-4255-a3dc-df62aa8bbfd3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=86405503-4a26-4cdc-a390-6693c14ecb45 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=e9c6bda8-e532-41aa-8055-940ad47d6840 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by oldfred on 2009-12-27
Your mount is not giving an error and this is there
/dev/sda7             333G  1.3G  315G   1% /home

You do not see it separately but it is there as /home and /home/sef. You should see sef (or whatever your user name is)

I mount my home from a separate partition and all I see is fred not /home/fred in the left panel.

---

### Post by Sef on 2009-12-28
Thank you fred... it seems i misread what I was seeing.

---

