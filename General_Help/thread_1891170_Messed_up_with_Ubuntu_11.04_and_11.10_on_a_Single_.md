---
title: "Messed up with Ubuntu 11.04 and 11.10 on a Single PC"
date: 2011-12-05
forum: General Help
---

### Post by rakesh.swapna on 2011-12-05
I messed up with Ubuntu versions 11.04 and 11.10.
Due to some problems in upgrading from 11.04 to 11.10 I have installed 11.10 on a new partion. 11.10 is working fine, but 11.04 occupied a lot of space. Help me to remove all old Ubuntu and keep only 3.0.0.13 generic. My GRBU looks like this...

Ubuntu, with linux 3.0.0.13-generic
Ubuntu, with linux 3.0.0.13-generic (Recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda2)
Windows 7 (loader) (on /dev/sda3)
Ubuntu, with linux 3.0.0.12-generic-pae(on /dev/sda7)
Ubuntu, with linux 3.0.0.12-generic-pae(Recovery mode)(on /dev/sda7)
Ubuntu, with linux 3.0.0.12-generic (on /dev/sda7)
Ubuntu, with linux 3.0.0.12 generic (Recovery mode)(on /dev/sda7)
Ubuntu, with linux 2.6.38.12-generic (on /dev/sda7)
Ubuntu, with linux 2.6.38.12-generic (Recovery mode)(on /dev/sda7)



Thankyou

---

### Post by jerrrys on 2011-12-06
You can use Gparted that is on the Ubuntu live CD to delete partitions.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gparted&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gparted&sa=Search&cof=FORID:9)

---

### Post by BC59 on 2011-12-06
Can you send us the result of this on a terminal?

```
sudo parted /dev/sda print
```

From the Grub image is diificult to tell if you have partitions with other Ubuntu versions.

---

### Post by rakesh.swapna on 2011-12-08
[QUOTE=BC59;11518004]Can you send us the result of this on a terminal?

```
sudo parted /dev/sda print
```

This is the result of parted


ammu@ammu:~$ sudo parted /dev/sda print
[sudo] password for ammu: 
Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   fat16           diag
 2      106MB   15.8GB  15.7GB  primary   ntfs            boot
 3      15.8GB  152GB   136GB   primary   ntfs
 4      152GB   500GB   348GB   extended                  lba
 7      152GB   256GB   105GB   logical   ext4
 8      256GB   261GB   4190MB  logical   linux-swap(v1)
 5      261GB   324GB   63.8GB  logical   ntfs
 9      324GB   376GB   52.1GB  logical   ext4
10      376GB   381GB   4195MB  logical   linux-swap(v1)
 6      381GB   500GB   120GB   logical   ntfs

---

### Post by BC59 on 2011-12-08
Ok I see. 

You have to delete sda7 and the second swap which is sda8. Then is going to be created empty "unallocated" space. 

Then you could expand sda5 ntfs to occupy the empty space, if you like.

To do all this, boot with a Live CD (ubuntu) and after you choose try, open the application GParted. From there you can delete the partitions.

---

### Post by rakesh.swapna on 2011-12-09
I have tried to delete the sda 7 and 8 but getting an error message 

[B]Unable to delete /dev/sda7[B]
Please unmount any logical partitions having
a number higher than 7

Please guide, wht to do next

---

### Post by BC59 on 2011-12-09
The only way to delete the partitions is when they are unmount. So you have to boot from a Live CD (the CD you installed Ubuntu) or a bootable USB and from there to open GParted and delete the partitions.

---

### Post by rakesh.swapna on 2011-12-09
I formated the sda7 using gparted. Made a new drive and using it. Thank you for the support.....

---

