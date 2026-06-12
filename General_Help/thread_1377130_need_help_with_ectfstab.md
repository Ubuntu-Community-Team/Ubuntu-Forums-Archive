---
title: "need help with /ect/fstab"
date: 2010-01-09
forum: General Help
---

### Post by bootdoc on 2010-01-09
I would like to mount a partition on a second disk as /home.  I have two hdds.  one is 250gigs that I wish to use for the / of two or more os'.   The other is 1TB that I would like to use as /home/charlie and /home/prisca as well as some other partitions.  Here is my current /etc/fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=a191ca61-57fe-41ad-ae9e-a29f9c60d1c6 /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=80630318-f158-4bdc-92b4-58f5336e6600 /boot           ext4    relatime        0       2
# /home was on /dev/sda7 during installation
UUID=8689305e-8ce8-4587-9345-f2e7f822abcb /home           ext4    relatime        0       2
# /var was on /dev/sda5 during installation
UUID=30c59fc9-0e99-4305-a02e-c4c77abdff0b /var            ext4    relatime        0       2
/dev/scd1         /media/cdrom0     udf,iso9660   user,noauto,exec,utf8   0       0
/dev/scd2         /media/cdrom2     udf,iso9660   user,noauto,exec,utf8   0       0
#/dev/fd0          /media/floppy0    auto      rw,user,noauto,exec,utf8   0       0
#/dev/sdc1	  /media/media1  	ext3  	rw,user,auto,noexec  	0	0
#/dev/sdc2  	/media/MEDIA2  	vfat	  rw,user,auto,noexec  	0	0
/dev/sdb5  	/media/charlie  	ext4  	rw,user,auto,noexec 	0	0
/dev/sdb6  	/media/prisca	        ext4	    rw,user,auto,noexec    	0	0
/dev/sdb7	        /media/music	        ext4	    rw,user,auto,noexec    	0	0
/dev/sdb8  	/media/videos  	ext4  	rw,user,auto,noexec    	0	0
/dev/sdb9	       /media/audio  	        ext4	        rw,user,auto,noexec    	0	0
/dev/sdb10	/media/video	        ext4	        rw,user,auto,noexec	  0	0
/dev/sdb11	/media/backup	        ext4	        rw,user,auto,noexec	  0	0

I want to take /dev/sdb5 and /dev/sdb6 and mount them as /home/charlie /home/prisca respectively.  /dev/sdb7 8 9 10 11 can remain as they are.  
First question is do I have to transfer everything in the existing /home to the new /home before changing the fstab?  question 2 is how do I make the other partitions usable by all users?

---

### Post by michy99 on 2010-01-09
You might want to read through this before you start.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

