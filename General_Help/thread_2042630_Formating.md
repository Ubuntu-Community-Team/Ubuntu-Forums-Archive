---
title: "Formating"
date: 2012-08-15
forum: General Help
---

### Post by KyleMich on 2012-08-15
I am trying to format an external drive (which was originally an old laptop drive)back to the NTFS format, but I ran into an issue right off the bat. I got this error once I clicked the "format" button in the disk utility program.

This is the error I get: 

Error creating file system: helper exited with exit code 1: helper failed with:
/dev/sdb is entire device, not just one partition.
mkntfs forced anyway.
Couldn't determine the size of /dev/sdb.  Please specify the number of sectors manually.


I have attached a screen shot (could be very useful, and may answer any questions you have.) I plan to take this laptop hard drive, and use it in my computer for windows (only to play some games that Ubuntu wont run) If it is any help, I am using Ubuntu 12.04 LTS. It is a 60GB Hard Drive, and I have no clue how to fix the error.

---

### Post by HermanAB on 2012-08-15
Hmm, try this:

Get the name of the device:
Plug it in
$ dmesg
Look for sdb, sdc, sdd...

Assuming sdb from here onward.

Delete the old partition data:
$ sudo dd if=/dev/zero of=/dev/sdb bs=1K count=1K

Create a new partition:
$ sudo fdisk /dev/sdb
n
p
enter
enter
enter
w

Format the partition:
$ sudo mkfs.vfat -n USBVFAT /dev/sdb1
or
$ sudo mkfs.ntfs -L USBNTFS /dev/sdb1

---

### Post by coldraven on 2012-08-15
You might get better results using Gparted. make sure that you select the correct drive from the drop-down menu in the top right hand corner of the window.
I would try deleting  the existing partition and create a new one, then format to NTFS.

---

### Post by KyleMich on 2012-08-15
when i get to the last step of formatting the partition, i get this error. 

kyle@Kyle-HP:~$ sudo mkfs.vfat -n USBVFAT /dev/sdb1
mkfs.vfat 3.0.12 (29 Oct 2011)
/dev/sdb1: No such file or directory
kyle@Kyle-HP:~$ 

kyle@Kyle-HP:~$ sudo mkfs.ntfs -L USBNTFS /dev/sdb1
Failed to access '/dev/sdb1': No such file or directory
The device doesn't exist; did you specify it correctly?
kyle@Kyle-HP:~$ 


How should I go about fixing this? It seems like it cant even be detected, I have no clue why. ):

---

### Post by HermanAB on 2012-08-15
Run fdisk again and verify the partition table of the device with the p command.  Press m for help.

---

### Post by dcstar on 2012-08-15
> **KyleMich said:**
> I am trying to format an external drive (which was originally an old laptop drive)back to the NTFS format,
.........

The drive is not even being detected correctly in the USB device, which is not surprising given it is an ancient 60GB device. It may well be faulty.

---

