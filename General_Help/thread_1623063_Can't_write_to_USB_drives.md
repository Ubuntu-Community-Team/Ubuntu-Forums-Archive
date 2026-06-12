---
title: "Can't write to USB drives"
date: 2010-11-16
forum: General Help
---

### Post by pbhill on 2010-11-16
After using my external hard drive for three or more years, I'm now getting a message telling me that I can't write to it. Same with my USB flash sticks.
They are all formatted in vfat. 
I recently upgraded to 10.10. Would this have something to do with it?
[LIST]
Why would write permissions change on their own?
[/LIST]
[LIST]
How do I get them back?
[/LIST]
This is seriously affecting my ability to work with Ubuntu and I'd rather not revert to Windows.
Thanks for any help

---

### Post by Hippytaff on 2010-11-16
You can use chmod to change permissions if that is the problem. Does ubuntu see the usb devices when they are plugged in?
```

lsusb

```
are the usb devices mounting properly?
with the devices plugged in type
```

mount

```
to see if they are mounted :-)

---

### Post by pbhill on 2010-11-16
Yes, I can see and read all the USB devices. (For some reason my USB hard drive is listed twice). Just can't write to any of them. And I can't change the permissions as they are owned by "root". I can't seem to change the ownership of any USB device either.

---

### Post by Hippytaff on 2010-11-17
you should be able to use your password to become root for a time using sudo
ie
```

sudo chmod rw /path/to/usb

```
 
Though I'm no longer sure it's a permissions thing. Can you post the output of lsub and we can have a look whats going on :-)

---

### Post by stefangr1 on 2010-11-17
As a quick fix (if you need to get something on it fast), you can always mount it manually with option umask=0.

E.g.: you check the location manually by running:

```
sudo fdisk -l
```

Than if you find your usb disk (for example) to be /dev/sdc1 (and /home/something an arbitrary empty folder where you can mount your usb disk), you run:

```
sudo mount /dev/sdc1 -t vfat, umask=0 /home/something
```

It was always my impression that this issue (which I have experienced as well occasionally) may be related to something going wrong with permissions when using an usb stick on multiple linux or osx systems. I'm not sure about this, though, and I don't know how to fix it.

---

### Post by pbhill on 2010-11-17
> **Hippytaff said:**
> you should be able to use your password to become root for a time using sudo
ie
```

sudo chmod rw /path/to/usb

```
 
Though I'm no longer sure it's a permissions thing. Can you post the output of lsub and we can have a look whats going on :-)

pbhill@Acer-Ubuntu:~$ lsub
No command 'lsub' found, did you mean:
 Command 'lsusb' from package 'usbutils' (main)
 Command 'qsub' from package 'gridengine-client' (universe)
 Command 'qsub' from package 'torque-client' (multiverse)
 Command 'qsub' from package 'torque-client-x11' (universe)
lsub: command not found
pbhill@Acer-Ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 006: ID 03f0:8704 Hewlett-Packard DeskJet 5940
Bus 003 Device 003: ID 0529:0001 Aladdin Knowledge Systems HASP v0.06
Bus 003 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 1058:0901 Western Digital Technologies, Inc. MyBook External HDD
Bus 001 Device 005: ID 046d:0892 Logitech, Inc. OrbiCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
pbhill@Acer-Ubuntu:~$

---

### Post by Hippytaff on 2010-11-17
I would tend to agree with stefang1 - manually mount if for the time being and look into resolving permissions issues

---

### Post by pbhill on 2010-11-23
I've solved the problem for the time being. After searching the web and Googling this problem for two weeks, I still hadn't found a good answer to the problem. 
My solution, and I hope it's temporary, is to install Windows in VirtualBox. Windows has no problem reading and writing to these USB drives! At least now I can bring work home again. I guess this shows why Ubuntu just isn't ready for "prime time".

---

### Post by nl4m on 2010-11-23
> **pbhill said:**
> I've solved the problem for the time being. After searching the web and Googling this problem for two weeks, I still hadn't found a good answer to the problem. 
My solution, and I hope it's temporary, is to install Windows in VirtualBox. Windows has no problem reading and writing to these USB drives! At least now I can bring work home again. I guess this shows why Ubuntu just isn't ready for "prime time".

When you boot from the LiveCD, pop the USB flash drive in and see if it mounts? If so, you can copy the mount files from the CD to your HDD. Push comes to shove, I can send you all of my mount files.

---

### Post by R4m4m on 2010-11-23
I had a similar problem and I used Gparted to format my USB sticks to fat32 and ubuntu 10.10 now reads them just fine

---

### Post by pbhill on 2010-11-24
> **nl4m said:**
> When you boot from the LiveCD, pop the USB flash drive in and see if it mounts? If so, you can copy the mount files from the CD to your HDD. Push comes to shove, I can send you all of my mount files.

Thanks! I will try this later after work!

---

### Post by pbhill on 2010-11-24
> **R4m4m said:**
> I had a similar problem and I used Gparted to format my USB sticks to fat32 and ubuntu 10.10 now reads them just fine

They are already fat32, as well as my USB hard drive. The problem started spontaneously as everything used to mount with all permissions. The problem I have is no write capability.

---

### Post by pbhill on 2010-12-10
OK, I finally figured out how to get the drive mounted at startup, by adding the appropriate line to /etc/fstab. (Actually copied someone else's line and it worked) But now whenever I boot up it takes *forever[I]*[/I]! It seems the whole 500GB disk has to be read before anything happens. It didn't used to do this. What have I done wrong? I'll post my fstab for review:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=8ce12373-3609-4aef-9d85-59a1b65b952b /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=a44c99b8-d52e-40cd-b649-357dcc13da53 /home           ext3    defaults        0       2
# /windows was on /dev/sdb1 during installation
UUID=BEEB-B809  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda6 during installation
UUID=75b659d5-bed9-45d1-8ae0-3b20533ff348 none            swap    sw              0       0
/dev/sdb1 /media/USB_STORAGE  vfat  rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,flush   0    0

---

### Post by kcpoole on 2010-12-27
What has changed in 10.10?

I have the same problem on and external hard disk I use for backup.

Previousely I used Ubunmtu 9.04, and my shell script on the External drive worked fine.
After installing U10.10, U can no longer execute the shell scripts on the drive, nor change the permissions on them
I amd the owner of the files on the drive and can create new files, and delete existing ones but no execute!

I do not mount the drive at permanately as it is my offsite storage so manually creating a mount in fstab is no good

Any way to revert to ?

Yet another thing thats broken it 10.10

ken

---

### Post by pbhill on 2010-12-28
I had to regress to 10.04 to get things working properly.

---

