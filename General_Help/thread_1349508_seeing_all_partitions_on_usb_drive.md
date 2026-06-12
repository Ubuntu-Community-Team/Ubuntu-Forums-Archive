---
title: "seeing all partitions on usb drive"
date: 2009-12-08
forum: General Help
---

### Post by slash5bmw on 2009-12-08
I am running ubuntu 9.1 on a laptop. I hooked up an external hard drive via an USB adapter and the laptop recognized the drive.

The problem is that ubuntu only sees the /boot partition on the external drive. The external drive had CENTOS installed on it and many other files. 

Is there a way to access the other files on my external drive?

I want to copy all the files off the external USB drive.

TIA

John

---

### Post by MaindotC on 2009-12-08
Post the output of:
```

sudo fdisk -l
lsusb

```
and please be kind and check the man pages of the commands I'm giving you.

---

### Post by slash5bmw on 2009-12-08
I plugged the drive in a usb port on my centos pc.
I ran your commands and it returned the following.
[root@localhost ~]# fdisk -l

Disk /dev/sda: 1600.3 GB, 1600320232960 bytes
255 heads, 63 sectors/track, 194561 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14      194561  1562706810   8e  Linux LVM

Disk /dev/sdb: 1600.3 GB, 1600320232960 bytes
255 heads, 63 sectors/track, 194561 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      104391   83  Linux
/dev/sdb2              14      194560  1562698777+  8e  Linux LVM
[root@localhost ~]# 
[root@localhost ~]# lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
[root@localhost ~]# 

When I use the gui to see what's on the disk, it mounts the usb with the label /boot and I can only see boot files.

Any ideas?

Thx

John

---

### Post by rahilm on 2009-12-08
try
sudo mount /dev/sdb2

its my best guess

---

### Post by MaindotC on 2009-12-09
Please enclose output from the terminal in tags:
```

It should look like this

```

The lsusb command shows that your drive is detected.  Does that match the manufacturer make and model?  According to the output of fdisk, it appears one of the drives is 1.6 TB in size and has two partitions on it.  When you plug in the drive, it should show in Places -> Computer from the drop-down menu.  Yes there will show a /boot partition which CentOS would have created by default (as most red hat-based systems do), but you should see the other partition as well and it should mount when you click on it.

If not, I suggest you do as rahilm suggested, depending on if the drive you are trying to view is /dev/sda or /dev/sdb.  You should see the drive you use natively on your machine in /etc/fstab.  There should be a section like this if sda is your main drive:
```

# /dev/sda1
UUID=0a51ac03-699e-41c9-a974-8a85c4d3257c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=a813f650-e68a-42a1-98f0-f3fb1dc38ed7 /home           ext3    relatime        0       2

```

There will also be an entry in /etc/mtab.  It looks like it's /dev/sdb and the partition that keeps mounting is /dev/sdb1.  Try mounting /dev/sdb2 instead.  You may need to create a mount point - a location to display the files in the partition.  An example would be:
```

sudo mkdir /mnt/part2
sudo mount /dev/sdb2 /mnt/part -t ext3 -o loop

```

---

