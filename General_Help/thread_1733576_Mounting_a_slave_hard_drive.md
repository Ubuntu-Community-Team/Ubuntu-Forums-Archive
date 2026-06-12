---
title: "Mounting a slave hard drive"
date: 2011-04-19
forum: General Help
---

### Post by rapattack1 on 2011-04-19
Hi I have installed Musix distro on my brand new amd 64 dual core computer but for some reason it is not showing in the media folder. Been a while since i mounted a slave and plain ubuntu seems to do it automatically so i forgot what commands i need to see it. Would love some help as the Musix forum is messed up. They have most of their forum in spanish and the parts that are english are not complete. I managed to sign up but that damn thing is really messed up. I signed up as over 18 but it sends you a form to have signed as under 18. Made 2 different users and still the same problem :0(

---

### Post by Irony on 2011-04-19
Use disk utility to see your drive and mount the drive.

Terminal wise something like;

```
sudo mount /dev/sda? ~/Desktop/afolder
```

should do it - note create afolder on your desktop or wherever.

---

### Post by seawolf167 on 2011-04-19
If you want to mount it automatically on boot, you can add an /etc/fstab entry to mount it for you. If you want to work through it yourself, take a look at the fstab link in my signature, else, post the output of 

```
blkid
sudo fdisk -l
mount
```

so we can help you

---

### Post by rapattack1 on 2011-04-19
Um i did this 
deb@deb-desktop:~$ sudo mount /dev/sdb ~/Desktop/afolder
[sudo] password for deb: 
mount: mount point /home/deb/Desktop/afolder does not exist

Not sure what to do next.
I do not know how to do it via the disk utility i am afraid. I am sure i have done it in the past but it has been a while. Always found it hard to find the info via google.

seawolf167-
deb@deb-desktop:~$ blkid
deb@deb-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ea3cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30346   243748423+  83  Linux
/dev/sda2           30346       60802   244635649    5  Extended
/dev/sda5           59877       60802     7426048   82  Linux swap / Solaris
/dev/sda6           30346       58675   227554304   83  Linux
/dev/sda7           58675       59877     9649152   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
deb@deb-desktop:~$ mount

Sorry not sure about the other stuff. The old brain is not very switched on today due to my disability so bear with me please.

---

### Post by dcstar on 2011-04-20
> **rapattack1 said:**
> Hi I have installed Musix distro on my brand new amd 64 dual core computer but for some reason it is not showing in the media folder. Been a while since i mounted a slave and plain ubuntu seems to do it automatically so i forgot what commands i need to see it. Would love some help as the Musix forum is messed up. They have most of their forum in spanish and the parts that are english are not complete. I managed to sign up but that damn thing is really messed up. I signed up as over 18 but it sends you a form to have signed as under 18. Made 2 different users and still the same problem :0(

Install the **pysdm** package.

---

### Post by rapattack1 on 2011-04-20
Thanks that is installed just will have to spend time understanding how to use it. the mount button is greyed out so unusuable to mount the slave.

---

### Post by seawolf167 on 2011-04-20
Assuming your "slave" drive is the 500GB /dev/sdb, you'll first want to format it with GParted. Assuming you format it in ext4, your /etc/fstab entry would look like this

```
/dev/sdb     /path/to/mount/point     ext4     defaults     0     2
```

Note that you need to create your mount point first

```
sudo mkdir /path/to/mount/point
```

Also, if you rerun *blkid* with *sudo*, you can replace the above /dev/sdb with that drive's unique UUID.

---

### Post by rapattack1 on 2011-04-20
Thanks but can you give me step by step instructions as i am not that good with it. Both hard drives are the same size. Yes i would say it is sdb. I know the slave is a western digital.
Sorry i know i have done this before but my medical condition doesn't allow me to remember. Most of the trouble before was that i was given incomplete information and then too much time would pass so was unable to retain it. Wish i could blame it on something bad i did to myself but nope :0)

---

### Post by Irony on 2011-04-20
> **rapattack1 said:**
> Um i did this 
deb@deb-desktop:~$ sudo mount /dev/sdb ~/Desktop/afolder
[sudo] password for deb: 
mount: mount point /home/deb/Desktop/afolder does not exist

Not sure what to do next.
Create a folder on your desktop first! i.e. right click on the desktop create a folder called 'afolder'.

---

### Post by rapattack1 on 2011-04-20
Ok done

---

### Post by seawolf167 on 2011-04-20
0. plug in your drive (if it isn't already)

1. format your drive by opening GParted (System -> Administration -> GParted), select your device (/dev/sdb), format it in ext4

2. make the directory for your mount point (replace /path/to/mount/point with the directory you want to mount it in)

```
sudo mkdir /path/to/mount/point
```3. open /etc/fstab for editing

```
sudo gedit /etc/fstab
```4. scroll to the bottom, add the entry for your drive to mount at your mount point created in #2

```
/dev/sdb     /path/to/mount/point     ext4     defaults     0      2
```Optional: If you rerun *blkid* with *sudo, *i.e.

```
sudo blkid
```You can replace the above /dev/sdb in step #4 that drive's unique UUID, i.e. instead of 

```
/dev/sdb
```it is

```
UUID=A854479B54476AE0
```(but replace it with your unique UUID from the previously mentioned optional step

---

### Post by rapattack1 on 2011-04-30
Hi sorry i didn't reply earlier. I was not getting anywhere so i reversed the order of the drives physically now everything seems to work well. The drive that had problems mounting is mounting now with seemingly no problems :))
I had reinstalled the oS several times and when i rebooted it still didn't do anything. So i thought i would just install on the new drive that came with the new machine and that worked. Then afterwards i put the older drive as a secondary and it mounted with a reboot and a click on the icon of the drive. Thanks so much :0)

---

