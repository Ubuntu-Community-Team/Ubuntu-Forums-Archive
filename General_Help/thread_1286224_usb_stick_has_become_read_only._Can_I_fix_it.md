---
title: "usb stick has become read only. Can I fix it?"
date: 2009-10-08
forum: General Help
---

### Post by HarmonicaGoldfish on 2009-10-08
I created a bootable usb stick to install jolicloud on my dell mini 9. It worked and I was able to install the os. The thing is that now I can no longer use the usb stick. I would like to be able to use it again but when I plug in the stick I can view the files but can not delete them. I am also unable to change permissions on the stick or any of the files contained on it. I have tried to do so both as root and as user. 

I created the stick on my dell inspiron 1525 when it was running 9.04. It now has the 9.10 beta. I can not even view the folder for the stick when it is plugged into that machine. 

Is the stick useless now?

Thanks!

---

### Post by pastalavista on 2009-10-08
You should be able to reformat the drive with gparted. After you install, it will be in the System > Administration menu.```
sudo apt-get install gparted
```

---

### Post by HarmonicaGoldfish on 2009-10-08
Thanks. I now have the usb in gparted.

Gparted tells me that it has an unallocated file system and that it is 964.84 MB, so what do I need to do in order to reformat it?

---

### Post by HarmonicaGoldfish on 2009-10-08
ok, so I tried it but no go. I tried to create a partition table, was warned that by clicking create I would erase everything on the stick. But once the process was complete the old files are still there and I still can't delete them or change permissions. Am I doing something wrong?

---

### Post by fragos on 2009-10-08
Click the unallocated space to select it. Menu Partition and click New. At this point I like to add a Label which will show as mountable in Nautilus. The other parameters are OK to use as is. Now click the Add button.

---

### Post by HarmonicaGoldfish on 2009-10-08
Thanks. I tried that but was met with an error.

mkdosfs unable to open /dev/sdb1

what does this mean?

---

### Post by fragos on 2009-10-08
mkdosfs is for creating MSDOS/Windows FAT file system under Linux. USB sticks come from the factory with FAT16 if 2GB or less and FAT32 if greater. I've never seen this error but I'm a user of and not an expert in disk partitioning.

---

### Post by HarmonicaGoldfish on 2009-10-09
I got it to work! Thanks for the help :)

---

