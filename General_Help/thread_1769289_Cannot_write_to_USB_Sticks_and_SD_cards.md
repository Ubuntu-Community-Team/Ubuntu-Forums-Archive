---
title: "Cannot write to USB Sticks and SD cards"
date: 2011-05-27
forum: General Help
---

### Post by Rog 3236 on 2011-05-27
I am running a dual boot system Ubuntu 10.04 (32 bit) and Windows 7 Home Premium (64 bit) on a Dell Inspiron 540s. I currently have an 8 GB USB stick inserted in a 4 port USB hub. I can read files on the device but I cannot write to any of the files. Using the ls and chmod commands I get the following outputs. Note that after assigning rwxr to all users nothing changes. Incidentally, since I could not write to the stick I created a text file in windows and saved it to the USB stick as a text file. 

rwhanson@ubuntu:~$ ls -l /media/usb/file3.txt
-rwxr-xr-x 1 root root 6 2011-05-27 15:17 /media/usb/file3.txt
rwhanson@ubuntu:~$ sudo chmod 777 /media/usb/file3.txt
[sudo] password for rwhanson: 
rwhanson@ubuntu:~$ ls -l /media/usb/file3.txt
-rwxr-xr-x 1 root root 6 2011-05-27 15:17 /media/usb/file3.txt
rwhanson@ubuntu:~$ 

I continuously receive the statement only root has the priviledge of writing etc. to the files on the USB stick. I have the same problem when I insert a card reader with an SD card. It is recognized but I do not have write priviledges.

Any help with this issue would be appreciated.

---

### Post by oldfred on 2011-05-27
If the USB stick is formated NTFS or FAT you cannot change ownership or permissions as NTFS does not support that.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
mount [http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt)
[http://www.mjmwired.net/kernel/Documentation/filesystems/vfat.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/vfat.txt)

---

### Post by Toz on 2011-05-27
I find that sometimes I can't write to non-NTFS USB sticks if there is an inconsistency in the file system. Linux seems to be more diligent than Windows at not allowing any sort of writing if a problem exists. If they are not ntfs, try running dosfsck against them to see.```
sudo dosfsck /dev/xxxx
```where xxxx is the device name.

---

### Post by Rog 3236 on 2011-05-28
Thanks after reading the links you provided I resolved the issue. I still have another issue to resolve but will use another post.

Roger

---

