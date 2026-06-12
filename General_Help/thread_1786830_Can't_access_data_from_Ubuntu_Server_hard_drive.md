---
title: "Can't access data from Ubuntu Server hard drive"
date: 2011-06-20
forum: General Help
---

### Post by dansin on 2011-06-20
My servers (10.10) motherboard has failed so to access my data I've taken the hard drive out and tried to connect to it via my ubuntu desktop (10.10).  I've tried it in a hard drive caddy and installed in my pc, but could only see a 255Mb Filesystem with a few folders and files on it.  Can anybody please help me to understand how to mount the portion of the disk that I can't see? Ie. the part with all of the data on it.

Thanks in advance

---

### Post by rbishop on 2011-06-20
Post the output of the following command with and without the "server" hard drive connected.

```

ls /dev/

```We are looking for a change in the list.  You should see at least one more entry in this list.  Start looking in the area where you see 

```

sda         
sda1        
sda2        
sda5        
sda6 

```Let us know if you have any questions.

---

### Post by dansin on 2011-06-20
The difference between the drive being connected or not are the additional entries - sdc1, sdc2 and sdc5.  I'm guessing 1 is the 255Mb partition, 2 is my data and 5 is a swap?  Still can't see or access sdc2 though.

---

### Post by rbishop on 2011-06-20
Try running the following list of commands... This should then allow you to mount the server hard drive.

```

cd /
mkdir server
mkdir server2
mkdir server3

sudo mount /dev/sdc1/ /server/
sudo mount /dev/sdc2/ /server2/
sudo mount /dev/sdc5/ /server3/


```

You should then be allowed to browse those folders.

---

### Post by dansin on 2011-06-20
> **rbishop said:**
> Try running the following list of commands... This should then allow you to mount the server hard drive.

```

cd /
mkdir server
mkdir server2
mkdir server3

sudo mount /dev/sdc1/ /server/
sudo mount /dev/sdc2/ /server2/
sudo mount /dev/sdc5/ /server3/


```You should then be allowed to browse those folders.

I had to use **sudo mkdir server2** to create the directory.

When I tried **sudo mount /dev/sdc2/ /server2/** I got [B]mount: you must specify the filesystem type
[/B] 
So I then tried **sudo mount -t ext2 /dev/sdc2/ /server2/** and then got [B]mount: wrong fs type, bad option, bad superblock on /dev/sdc2,missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail  or so
[/B]
I also tried ext3 and ext4 with the same result.

I've also changed the boot order in the bios to boot the server disk first and it boots fine.  I can log on and list my folders but I can't then transfer anything as it doesn't see the desktop hard drives... :(

---

### Post by jm2 on 2011-06-20
To find out the disk type:

at the command prompt type:

sudo fdisk -l

this should list the /dev/sd? and the last column is the file type.

When you run mount, it defaults to read only, I believe. You might need to change the 
the permissions on the directory where you are mounting the drive to.

ie: sudo chmod 700 /mnt/server2

and/or change the owner on the /mnt/server2 to your name.
sudo chown <myname> /mnt/server2

Just a few quick thoughts to help.

---

### Post by bodhi.zazen on 2011-06-20
Well, what partition are you trying to mount ? From the earlier posts it did not appear you knew what partition was the data partition and what was swap.

Try :```
sudo blkid
```

Then mount your partitions and transfer the data, can be done from either server or desktop.

mkdir /mnt/mount_point
mount /dev/sdxy /mnt/mount_point
cp -R /mnt/mount-point/your_data /destination

---

### Post by dansin on 2011-06-21
> **jm2 said:**
> To find out the disk type:

at the command prompt type:

sudo fdisk -l

this should list the /dev/sd? and the last column is the file type.

When you run mount, it defaults to read only, I believe. You might need to change the 
the permissions on the directory where you are mounting the drive to.

ie: sudo chmod 700 /mnt/server2

and/or change the owner on the /mnt/server2 to your name.
sudo chown <myname> /mnt/server2

Just a few quick thoughts to help.

> **bodhi.zazen said:**
> Well, what partition are you trying to mount ? From the earlier posts it did not appear you knew what partition was the data partition and what was swap.

Try :```
sudo blkid
```Then mount your partitions and transfer the data, can be done from either server or desktop.

mkdir /mnt/mount_point
mount /dev/sdxy /mnt/mount_point
cp -R /mnt/mount-point/your_data /destination

Thanks chaps.  You got me heading in the right direction.  The filesystem was LVM.  I used [http://www.linux-sxs.org/storage/fedora2ubuntu.html](http://www.linux-sxs.org/storage/fedora2ubuntu.html) to solve it.[]("http://www.linux-sxs.org/storage/fedora2ubuntu.html")

---

