---
title: "[EXT4] 600GB Disk Usage Discrepancy"
date: 2010-01-26
forum: General Help
---

### Post by adbge on 2010-01-26
Gparted reports that /dev/sdb2 has used 908 GiB / 931 GiB, while:

robb@britain:~$ sudo df -h /dev/sdb2
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2             361G  338G  4.6G  99% /home

is reporting 361GB / 338GB has been used. In fact, all of Ubuntu besides gparted reports these statistics.

What's going on?

---

### Post by vinnywright on 2010-01-26
post the output of 

> parted (after it starts type)

> print all

and it will display all disk's/partition's


and 

> df -h no sudo or /dev

VINNY

---

### Post by adbge on 2010-01-26
Parted output
> 
robb@britain:~$ sudo parted
(parted) print all
model: Ata patriot memory 3 (scsi)
disk /dev/sda: 32.0gb
sector size (logical/physical): 512b/512b
partition table: Msdos

number  start   end     size    type     file system     flags
 1      32.3kb  510mb   510mb   primary  linux-swap(v1)
 2      510mb   32.0gb  31.5gb  primary  ext4            boot


model: Ata hitachi hdt72101 (scsi)
disk /dev/sdb: 1000gb
sector size (logical/physical): 512b/512b
partition table: Msdos

number  start   end     size    type     file system  flags
 2      32.3kb  1000gb  1000gb  primary  ext4

warning: Unable to open /dev/fd0 read-write (read-only file system).  /dev/fd0
has been opened read-only.

Error: /dev/fd0: Unrecognised disk label 
(parted)
df -h output
> 
robb@britain:~$ df -h
filesystem            size  used avail use% mounted on
/dev/sda2              29g  4.3g   24g  16% /
udev                  2.0g  324k  2.0g   1% /dev
none                  2.0g  216k  2.0g   1% /dev/shm
none                  2.0g  288k  2.0g   1% /var/run
none                  2.0g     0  2.0g   0% /var/lock
none                  2.0g     0  2.0g   0% /lib/init/rw
/dev/sdb2             361g  338g  4.6g  99% /home


---

