---
title: "Added HDD Corrupts fstab"
date: 2011-01-31
forum: General Help
---

### Post by Sugi on 2011-01-31
I have added a new sata HDD and this caused my fstab to becoming corrupted.  I opened the fstab within a live cd and I changed it to the new setup.  But I am still getting an error.

My old setup:
sda on PATA
Windows 7
Linux /root
Linux swap

sdb on PATA
Linux storage

New setup with Sata HHD:
sda
New HDD *linux storage

sdb
Windows 7
Linux /root
Linux swap

sdc
Linux storage

As you see, the new HDD changed the order of the setup, but even if everything is changed, I can't get it to startup correctly.  On the new setup, I can get to grub and auto-pick linux, but I haven't tried Windows 7... How do I fix this?  Do I have to fix grub too?

Note: I'll upload my fstab and such when I get back home.

Didn't help:
[http://www.uluga.ubuntuforums.org/showthread.php?t=1565146](http://www.uluga.ubuntuforums.org/showthread.php?t=1565146)

Ubuntu 10.10 x64
HDDide:M:Win 7 / Lin S:Linux Storeage
HDDsata:Linux Storage
Sugi

---

### Post by TheHackOps on 2011-01-31
Waiting for your fstab, but i think i know the fix :)

---

### Post by Sugi on 2011-02-01
My fix fstab: [This should be correct, I had to redo it from hand.]
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
/dev/sdb5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
/dev/sdb6 /    none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# / on /dev/sdb1 not during installation
/dev/sdc1       /media/Stor1       ext3    rw,users        0       2
# / on /dev/sda1 not during installation
/dev/sda1       /mnt/Stor2       ext3    rw,users        0       2
```

My Current fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=51455f7d-efa4-4f3e-b81f-7b6986627f29 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=27304bee-6111-4102-b19d-36fd6eea7ca9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# / on /dev/sdb1 not during installation
/dev/sdb1       /media/Stor1       ext3    rw,users        0       2
```

**fdisk**
Normal boot, console mode:
```

sudo fdisk -l

Disk /dev/sda:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       91202   732572672   83  Linux

Disk /dev/sdb: 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13        3825    30617600    7  HPFS/NTFS
/dev/sdb3            3826        9729    47423880    5  Extended
/dev/sdb5            3826        9667    46925833+  83  Linux
/dev/sdb6            9668        9729      497983+  82  Linux swap / Solaris


Disk /dev/sdc: 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux
```

With the Live Disc,
```
sudo fdisk -l

Disk /dev/sda:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        3825    30617600    7  HPFS/NTFS
/dev/sda3            3826        9729    47423880    5  Extended
/dev/sda5            3826        9667    46925833+  83  Linux
/dev/sda6            9668        9729      497983+  82  Linux swap / Solaris

Disk /dev/sdb: 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91202   732572672   83  Linux

Disk /dev/sdd:
   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               3        5857     4007580    c  W95 FAT32 (LBA)
```

Sugi

---

### Post by vanadium on 2011-02-01
Use UUID references throughout in your /etc/fstab.You still refer to sdb1 using the device name. Also change that reference to a reference to the UUID.

---

### Post by Sugi on 2011-02-01
But it's ok to use /de/sdXX, right? UUID numbers isn't required?  Is there a way, to change my fstab from console?  It doesn't let me access it with sudo command.  What's the command for seeing all UUID?
blkid -o value -s UUID & blkid doesn't work

Sugi

---

### Post by matt_symes on 2011-02-01
Hi

> But it's ok to use /de/sdXX, right? UUID numbers isn't required? 

True; UUID's are safer than device names (these can change).

> Is there a way, to change my fstab from console? It doesn't let me access it with sudo command. 

Open a terminal, or from the console, type (assuming you have nano)

```
sudo nano /etc/fstab
```

Post back any error messages.

> What's the command for seeing all UUID?

From the terminal again type (requires a sudo)

```
sudo blkid
```

Post back any error messages or result.

Kind regards

---

### Post by vanadium on 2011-02-01
> **Sugi said:**
> But it's ok to use /de/sdXX, right?
What I was trying to tell, is that it is NOT OK. On some hardware, device names may change even between different boots!

The most convienient way to obtain your UUIDS is:
```

sudo blkid

```
The UUID is presented in a form that you can directly copy into your /etc/fstab.

To change fstab from a console, you need to load it into an editro of your choice. Console editors that are standard in Ubuntu are nano (easy to use) and vi (very standard, present on every unix system, very powerfull, but you need to learn that one).

---

### Post by Sugi on 2011-02-01
I can't make any changes / use sudo when my fstab isn't working correctly.  I keep having to use a live cd to make any changes to my files.

Sugi

---

### Post by matt_symes on 2011-02-01
Hi

> I can't make any changes / use sudo when my fstab isn't working correctly.

What do you mean ? Is sudo is not working ? Are you a member of the sudo and admin groups ?

Open a terminal and type

```
sudo -i
```

Enter your sudo password. Does this give you a root prompt ? If it does you can edit the file without using sudo.

```
nano /etc/fstab
```

Kind regards

---

### Post by vanadium on 2011-02-01
He is working from a live session. Thus, "nano /etc/fstab" won't load the correct fstab, i.e., the fstab belonging to his system installed on the hard disk.

---

### Post by matt_symes on 2011-02-01
Hi

> He is working from a live session.

Somehow i managed to miss that. It was mentioned twice as well. I must be getting old. :frown:

Kind regards

---

### Post by Sugi on 2011-02-03
I have made more changes to fstab, and I am still getting problems.
On boot-up error:
> Waiting on one or more mounts in the fstab:
/dev/disks/
/tmp: waiting for [null]

:waiting for 1
/media/Stor1: waiting for UUID=a40a10e0-45cb-46be-a5d5-4e42ce9d1559

Here's the copy of my fstab and blkid
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation [Old Setup doesn't work with New HDD]
UUID=51455f7d-efa4-4f3e-b81f-7b6986627f29	/               ext4    errors=remount-ro 0  
     1
# swap was on /dev/sda6 during installation [Old Setup doesn't work with New HDD]
UUID=27304bee-6111-4102-b19d-36fd6eea7ca9	 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /mnt/sdb1 on /dev/sdb1 not during installation
UUID=a40a10e0-45cb-46be-a5d5-4e42ce9d1559       /mnt/sdb1       ext3    rw,users        0       2

```

> 
sudo nano /etc/fstab
When I try to save, I get this message "[ Error writting /etc/fstab: Read-Only file system ]

sudo cp /etc/fstab /etc/fstab.1
cp: cannot create regular file '/etc/fstab.1': Read-only file system

Sugi

---

