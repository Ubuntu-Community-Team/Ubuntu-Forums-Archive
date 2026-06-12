---
title: "[B] Need Help Mounting Another HDD[B/]"
date: 2009-08-05
forum: General Help
---

### Post by priestscientist on 2009-08-05
Yes I am having a problem mounting another hard drive onto Linux. My second hard drive is detected but when I try to access the second drive, I get the message that I don't have Permission to access this drive "hdb". I looked into my /etc/fstab and /ect/mtab, and neither file shows that there is a hdb(second hard drive). Now here is the thing, The second drive is a ext3 file system, I am trying to gain access to it so I can back up my importaint files so I can reinstall my OS. My Second Drive is on the Slave drived (IDE). Now there are 3 things that I want to get resolved. **First:** I know that you can change permissions to a file by using 'chmod' command but I am having a hard time finding where exactly the second drive for me to change permissions because I do not see the second disk in /dev, and is it really the 'chmod' command the same as it is for files when it comes to change permissions to gain access to hdb(devices)? **Second:**If chmod can be used as well for devices please show me how it is suppose to look. **Third:** Dose the /etc/fstab and/or /etc/mtab needs to be modified, then how shold it look? Thank You very much

---

### Post by merlinus on 2009-08-05
```
sudo fdisk -l
```

should show the drive and partition in question.  Then if you wish it to automount with read/write permissions, you can add an appropriate entry to /etc/fstab.

---

### Post by priestscientist on 2009-08-05
Thank You. Hmmm What would an appropriate entry to /etc/fstab look like?

---

### Post by merlinus on 2009-08-05
/dev/sdb1 /media/sdb1 ext3 relatime 0 2

You will of course have to manually create whatever mountpoint you wish, and change /media/sdb1 to reflect this.

---

### Post by doas777 on 2009-08-05
what you probably want to do is create a line in your fstab for your new hdd.
first I usually run ```
sudo fdisk -l
``` to first determine what the drives device name is (/dev/sdXY). 

once I've found the drives /dev name, I check its UUID
```
 sudo vol_id /dev/sda1
``` and copy the parameter "ID_FS_UUID" to the clipboard.

now i open fstab with ```
sudo gedit /etc/fstab
```
and add a line at the bottom like:
```
UUID=<the uuid you copied>   <mount point>   <filesys type(ext2/3)>   relatime   0   0
```

adn reboot. then my drive is usually mounted at the point I specified. make sure that whereever you choose to mount it, that the directory exists, and is accessible by root.

have fun

---

### Post by priestscientist on 2009-08-05
Thank You Very Much I will definately implement this and see how this will unfold. Thank you very much for the info.

---

