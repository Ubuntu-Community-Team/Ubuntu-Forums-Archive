---
title: "Booting from USB stick, hard drives not auto mounting"
date: 2012-03-21
forum: General Help
---

### Post by cathalmccabe on 2012-03-21
Hello,
I want to run a media server using Ubuntu, and boot it from a USB stick. My sata hard drives are not auto mounting. I have to open (double click) each drive for it to be mounted. I have installed storage device manager, and explicitly configured each drive to mount on boot, but this does not seem to have any effect. It also does not seem to save the configuration between boots. Any suggestions? Is this because I a booting from USB or am I missing something?
I do have a persistent file partition on the USB stick.
Any suggestions appreciated.

---

### Post by aura7 on 2012-03-21
Try to mount them manually using 
fdisk -l
 
and then from the result
 
mkdir <some-dir>
mount /dev/sd** /media/<some-dir>

---

### Post by cathalmccabe on 2012-03-21
> **aura7 said:**
> Try to mount them manually using 
fdisk -l
 
and then from the result
 
mkdir <some-dir>
mount /dev/sd** /media/<some-dir>

fdisk -l
Returns nothing.

I know the drive I want to mount, so I run
sudo mount /dev/sda2 /dev/<folder> and it mounts it correctly (as it does when I open the drive in folder view by double clicking.)

When I reboot, the drive needs to be mounted again.

By the way, the disk is ext4 if this is relevant.

---

### Post by oldfred on 2012-03-21
If your flash drive is 8GB or more, it would be easier to have a full install on the flash drive. 

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

I do not think your persistent install saves settings as the install image is what is booted. The persistent install just lets you save data where a liveCD/USB without persistence does not let you save data.

But why not an install on the SATA drives, it does not have to be large.

I use these reasons, but install Ubuntu not Knoppix.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

