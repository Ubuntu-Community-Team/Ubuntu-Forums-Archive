---
title: "Mp3 -Failed to play: Could not open resource for writing."
date: 2006-03-08
forum: General Help
---

### Post by Jaylon on 2006-03-08
Hello there. I've installed gstreamer0.8-mad, but am getting this error message when trying to open an mp3 in totem or rhythmbox. Google etc has turned up nowt. Any ideas?

Sound is working on my system, and I can play WMA embedded in a website.

---

### Post by frodon on 2006-03-08
Maybe it's a right problem, what file system use the partition where your mp3 file is (FAT32, NTFS, ext3, ...).
What fstab line do you use to mount this partition ?

PS: to open your fstab file use this command : ```
sudo gedit /etc/fstab
```

---

### Post by Jaylon on 2006-03-08
I don't think that's it - I tried moving the file to my home folder and it didn't work either...have also checked the permissions are set to my username and that execute is ticked.

My fstab file looks like the following - the original partition was hda8 and is ext3.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda5       /media/hda5     vfat    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hda8       /media/stuff    ext3    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  ext,vfat    rw,user,noauto  0       0 

---

### Post by Jaylon on 2006-03-08
It's actually giving the same message when I try and play downloaded WMA files (rather than embedded) :confused:

---

### Post by frodon on 2006-03-09
Really strange, no idea for the moment.

Anyway you could edit your fstab file and modify your vfat lines like that : [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by Jaylon on 2006-03-09
No worries. Thanks anyway mate.

---

### Post by Seandq on 2006-03-10
[quote=Jaylon]No worries. Thanks anyway mate.[/quote]

I resolved this problem by restarting ESD.

> 
# killall esd
# esd &


---

### Post by melissawm on 2006-03-12
OK starting esd solved the problem momentarily (it wasn't running before that) but does that mean that everytime I start rhythmbox i'll have to start esd manually??

---

### Post by armando-leal on 2006-04-26
I had the same problem, and found that it was effectively caused by esd. But the real source of the problem was that i had just changed the default sound card, in the "sound preferences". Since i had no longer the the card that i chose as default, the esd wasn't loaded. As most of the new media players depend on this none of them worked, although the older ones (xmms) did.
Just correcting the default card and starting esd solved the problem.

---

