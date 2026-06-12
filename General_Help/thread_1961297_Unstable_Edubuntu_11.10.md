---
title: "Unstable Edubuntu 11.10"
date: 2012-04-19
forum: General Help
---

### Post by viktorjano on 2012-04-19
The Edubuntu 11.10 shows very unstable on my PC. Few months ago it lost connection with the mouse, and I had to reinstall the OS again. Now, it happens same thing with the usb ports. I can not mount usb stick on my computer, it does not recognize it at all. 

Does anyone has explanation for this issue, or it is just what I think, that this version of edubuntu is unstable!

---

### Post by codemaniac on 2012-04-19
Reinstalling the OS should be the last option in this whole wide world .
can you please plug your usb devices again and post the out put of lsusb .
On a terminal do this 
```
lsusb
```

---

### Post by viktorjano on 2012-05-02
Here is the output of that command:

> sskt-linux@ssktlinux:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1005:b113 Apacer Technology, Inc. Handy Steno 2.0/HT203
sskt-linux@ssktlinux:~$ 

So, on the bus 001 it recognizes the usb stick, but I don't know why it does not mount it on a folder. Usually, as you stuck the usb in the port it appears on the desktop!

---

### Post by codemaniac on 2012-05-02
Are you facing the same luck with other usb storage devices or other flash drives ?

---

### Post by viktorjano on 2012-05-03
Well I don't have any other flash drives in the moment. I can try that... But can you tell me what the problem might be?

---

### Post by viktorjano on 2012-05-03
And with the other usb drives, YES. Whatever usb drive I stuck, same thing.

---

### Post by codemaniac on 2012-05-03
Sometimes devices don't automount, in which case you should try to manually mount it. First, you must know what device we are dealing with and what filesystem it is formatted with. Most flash drives are FAT16 or FAT32 and most external hard disks are NTFS.

```
sudo fdisk -l
```
Find your device in the list, it is probably something like /dev/sdb1.

Now you need to create a mount point for the device, let's say we want to call it "external". You can call it whatever you want, just please don't use spaces in the name or it gets a little more complicated - use an underscore to separate words (like "my_external"). Create the mount point:

```
sudo mkdir /media/external
```
You can now mount the drive. Let's say the device is /dev/sdb1, the filesystem is FAT16 or FAT32 (like it is for most USB flash drives), and we want to mount it at /media/external (having already created the mount point):

```
sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
```
The options following the "-o" allow your user to have ownership of the drive, and the masks allow for extra security for file system permissions. If you don't use those extra options you may not be able to read and write the drive with your regular username.

Otherwise if the device is formatted with NTFS, run:
```
sudo mount -t ntfs-3g /dev/sdb1 /media/external
```
You must have the ntfs-3g driver installed.

---

### Post by viktorjano on 2012-05-03
Ok thanks...
 But do I have to do this every time I use usb flash disk?

---

### Post by codemaniac on 2012-05-03
I am afraid yes . you need to if it is not automouted .

---

