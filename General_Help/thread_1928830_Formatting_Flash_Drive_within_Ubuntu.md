---
title: "Formatting Flash Drive within Ubuntu"
date: 2012-02-20
forum: General Help
---

### Post by joeturtle on 2012-02-20
I purchased a new flash drive today because I somehow managed to lose my other one. (I needed the flash drive to use GParted to make way for another linux installation). So I got GParted to work and that's all good...so I thought I would format the device to get rid of GParted and not have to worry about deleting all the files and folders by hand...

And so I loaded the other Linux distribution onto the flashdrive, and it didn't work. So I reformatted and tried again. But this time, it wouldn't reformat. I tried using the Disk Utility that comes with Ubuntu and GParted to format the device. Both give me errors...and I tried using Google, but nothing I've read has helped thus far. So I'm reaching out to you to see if my problem can be solved. 

When I try to format the USP Drive in the Disk Utility, this message appears: "Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on /dev/sdb: Input/output error"

Within GParted, I receive a "Delete /dev/sdb2 (ext3, 953.49 MiB) from /dev/sdb  00:00:00    ( ERROR )
     	
calibrate /dev/sdb2  00:00:00    ( SUCCESS )
     	
path: /dev/sdb2
start: 3905504
end: 5858255
size: 1952752 (953.49 MiB)
delete partition  00:00:00    ( ERROR )
libparted messages    ( INFO )
     	
Input/output error during write on /dev/sdb
Error fsyncing/closing /dev/sdb: Input/output error"

If anyone can offer help in this matter, it would be much appreciated! Thank you!

---

### Post by dcstar on 2012-02-21
> **joeturtle said:**
> 
.........
If anyone can offer help in this matter, it would be much appreciated! Thank you!

It is probably broken.

---

### Post by 3rdalbum on 2012-02-21
It looks like a dud. A flash drive should not fail so quickly.

---

