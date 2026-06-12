---
title: "USB Drives mounted as Read Only.. Why?"
date: 2012-01-24
forum: General Help
---

### Post by dleric on 2012-01-24
Just reinstalled Ubuntu 11.10 and now my USB drives are being automatically mounted  as read only. I used to be able to Read, write, delete...  what ever. Now I can only copy. 

Please help.

---

### Post by linux4human on 2012-01-24
yeah i had this problem, did you try to update your manager ? ? ? maybe thats the problem try updating all your stuff and reboot and see if that work... there is a program a mount program that u can setup all ur mount to read and write... i had this problem before, and i install that program and config it and my usb stick work... but i also update stuff to but this is a known issue.. try to update everything and let me know if its still doing.. like update + reboot and try it if its still doing it... ill try to help you out...

---

### Post by linux4human on 2012-01-24
umm try to login root and see if u can write on ur usb.... if its not working in root i think perhaps ur drive is messed up or... try to use disk utility and unmout ur usb drive format FAT or NTFS and see if it write again or read or both .. hope that helps

---

### Post by Toz on 2012-01-24
You might also be able get some diagnostic information from your /var/log/syslog file. Plug in the usb drive and then look at the last 10-20 lines of that file to see if any problems are identified.

---

### Post by dcstar on 2012-01-25
> **dleric said:**
> Just reinstalled Ubuntu 11.10 and now my USB drives are being automatically mounted  as read only. I used to be able to Read, write, delete...  what ever. Now I can only copy. 


Use gparted or the Disk Manager to do a "Check" on the partitions.

---

### Post by ghlargh on 2012-01-25
I have had this problems a few times after not properly unmounting drives, mostly from using faulty USB hubs, but also from accidentally pulling the wrong USB cable.

I eventually fixed it using fsck. Please note that FAT drives need to be fixed with dosfsck.

---

### Post by stefangr1 on 2012-01-25
As a temporary solution (or if fixing won't work), you can always mount it manually with umask=0.


First, you run
```
fdisk -l
```
to see whether you can find your usb stick in the list that comes out. Say your usb stick has one partition on it that is called /dev/sdb1

You can then mount it with
```
sudo mount -t vfat -o umask=0 /dev/sdb1 <mount point>
```

---

