---
title: "HELP !! USB will not mount read/write!"
date: 2011-03-10
forum: General Help
---

### Post by KaYnemO on 2011-03-10
Hi all,

sudden of all all USB drives and sticks I put into a PC will not mount with read/write permissions (they did before). I can still copy to them, but only when I am root. I am on Maverick - please advise !!

I've noticed though that if I run disk utility, then UNMOUNT the partition, Check File System, Mount the partition back, I get read/write access....... Any thoughts ?

---

### Post by KaYnemO on 2011-03-14
*bump*

---

### Post by Kirboosy on 2011-03-14
You should be able to chmod the file in order to change the permissions.

```
sudo chmod 777 /media/[usb drive]/
```

An explanation of the numbers can be found [here]("http://www.pageresource.com/cgirec/chmod.htm")

---

### Post by KaYnemO on 2011-03-14
> **Caboose885 said:**
> You should be able to chmod the file in order to change the permissions.

```
sudo chmod 777 /media/[usb drive]/
```

An explanation of the numbers can be found [here]("http://www.pageresource.com/cgirec/chmod.htm")

I guess so, however, how do I fix the problem eternally and make the box act towards the USB devices as it used to ? I mean I never had to actually chmod the disks before (except very early in the linux life)...

---

### Post by vanadium on 2011-03-14
1) should not be necessary 2) May not be possible with ntfs volumes.

You may have usbmount installed. Remove it. See here: [http://ubuntuforums.org/archive/index.php/t-1478368.html](http://ubuntuforums.org/archive/index.php/t-1478368.html) (the end of hte thread is most relevant)

---

### Post by Kirboosy on 2011-03-14
The thumb-drive is probably a FAT or FAT32 Drive.

---

### Post by KaYnemO on 2011-03-14
Hmm.... what really bothers me is that this was not an issue only recently... could it have been some update that borked that ?

---

### Post by Kirboosy on 2011-03-14
Yeah its very possible...I can't think of one off the top of my head of an update that would break it though....

---

### Post by KaYnemO on 2011-03-14
o btw I've checked and the USBmount is not installed

---

### Post by vanadium on 2011-03-14
Load command terminal, unmount the drive and mount it manually. Error messages may provide a clue to the problem.

---

### Post by Hector23 on 2011-03-14
Would this help?

"User Privileges

If your usb device doesn't appear on your desktop, you should check that your user has the correct privileges. Go to System->Administration->User and Groups, choose the user, click on "Properties", then go to the "User Privileges" tab. You should have the "Access external storage devices automatically" option checked."

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

or anything on this page?

---

### Post by KaYnemO on 2011-03-16
OK this is driving me completely nuts !!!

1. User priviliges are fine - under this account I can do whatever I want.

2. Nothing mounts right - only after starting disk utility, unmounting, checking file system (on any usb drives at all),then mounting it back I get access to write (or under root). However the speed of transfer is really low. (on this pc I got 12 hours estimated time transferring 8 gb from one usb device to another, while on the much older pc with the same maverick I got it done in 17 minutes). So arrrgghhh !! I have no idea what I have done !!

To keep in mind, I get random errors that state that this device is already mounted, something like this:
> 
Unable to mount 21 GB Filesystem

Error mounting: mount exited with exit code 18: Failed to write lock '/dev/sdb1': Resource temporarily unavailable
Error opening '/dev/sdb1': Resource temporarily unavailable
Failed to mount '/dev/sdb1': Resource temporarily unavailable but it still mounts, or after remounting I get the name of the device with -1 attached and both (the old and the new mount points) lead to the same information !!!

Could I perhaps post the output of some command to you all ???? This is really driving me bugshit !!

Also - I seem to be unable to mount via terminal (either nothing changes or I get an error - no /media/[name] exists.

---

### Post by vanadium on 2011-03-17
* First show how the drive is mounted with the command
```

mount

```
* Show the permissions and ownership of the mount point with the command
```

ls -l /media

```
* Show how the system recognizes the drive with
```

sudo fdisk -l

```
* If it is indeed /dev/sdb1 that is concerned here, try following commands in order to attempt a manual mount (we first unmount the drive and unmount it again after we are done)
```

sudo umount /dev/sdb1
mkdir test
sudo mount /dev/sdb1 test
touch /test/testfile
ls -ld /test/testfile
sudo umount /dev/sdb1

```
* Look at how the kernel reacts when automounting the drive: Plug the drive off, then plug it back in, then:
```

dmesg | tail -n30

```

---

