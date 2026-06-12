---
title: "mounting partitions"
date: 2006-05-16
forum: General Help
---

### Post by fcastillo on 2006-05-16
I having problems with a partition that I have. I have a hard drive with ext3 file system, I can mount it and everything but I don't have write permission, after trying to solve the problem now i can't even mount it, only us root. You can see my fstab file that i put it as an attachment. The hard drive with problems is:

/dev/hdc2	/media/music	ext3		rw,user,auto			0	0

---

### Post by aysiu on 2006-05-16
For those too lazy to click the link: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  	<options>       		<dump>  <pass>
proc            /proc           proc    	defaults        		0       0
/dev/hdc1       /               ext3    	defaults,errors=remount-ro 	0       1
/dev/hdc5       none            swap    	sw              		0       0
/dev/hdd        /media/cdrom0   udf,iso9660 	ro,user,noauto  		0       0
/dev/hda        /media/cdrom1   udf,iso9660 	ro,user,noauto  		0       0
/dev/hdb        /media/cdrom2   udf,iso9660 	ro,user,noauto  		0       0
/dev/fd0        /media/floppy0  auto    	rw,user,noauto  		0       0
/dev/hdc2	/media/music	ext3		rw,user,auto			0	0
``` So it's /media/music you're trying to get?

Change the line to ```
/dev/hdc2 /media/music ext3 defaults 0 0
``` Then, paste these commands into a terminal ```
sudo umount /dev/hdc2
sudo mount -a
sudo chown -R fcastillo:fcastillo /media/music
sudo chmod -R 755 /media/music
```

---

### Post by Ramses de Norre on 2006-05-16
Mount it with a line similar to this: ```
/dev/hda4       /home               ext3    nodev,nosuid 0       2
```

---

