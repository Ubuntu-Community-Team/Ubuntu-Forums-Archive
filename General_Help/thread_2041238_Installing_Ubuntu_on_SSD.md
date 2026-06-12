---
title: "Installing Ubuntu on SSD"
date: 2012-08-12
forum: General Help
---

### Post by Nardon on 2012-08-12
Hello everyone!

In my laptop I have a 128GB SSD and a 500GB normal hard drive. It is running Windows 7 right now and want to create a dualboot with Ubuntu 12.04. 

Right now the whole SSD is used as the C drive where I only store system settings and programs and stuff. I have all my other data like documents, music, games and movies on the larger hard drive. What would be the best way to install Ubuntu on this setup? Any recommended partition settings or something like that?

Also, how well does Ubuntu support SSD's actually? Does it have functions like trimming and stuff?

Hope someone is able to help me!

---

### Post by jim_deadlock on 2012-08-12
Ubuntu works great with SSD, you can set the trim options in /etc/fstab like this:

```
# <file system> 			  <mount point>   <type>  <options>       			<dump>  <pass>
proc				          /proc           proc    nodev,noexec,nosuid 			0       0
tmpfs					  /tmp		  tmpfs	  defaults,noatime,mode=1777		0	0
tmpfs                                     /var/tmp	  tmpfs	  defaults,noatime,mode=1777		0	0
UUID=7944a180-602b-4e65-b863-39726ad07b0a none            swap    sw              			0       0
UUID=3b1723cb-088f-4380-9e66-e8cd9fcc775f /               ext4    noatime,discard,errors=remount-ro 	0       1
UUID=2fc889b2-c230-4e03-9e8e-1245f08d0101 /home           ext4    defaults        			0       2

```

Note noatime,discard on / which is my SSD with trimming. The tmpfs lines are optional.

What I recommend is to install the Ubuntu system on your SSD and put the /home partition on your HDD. So boot from a live CD and fire up Gparted. Resize your Win partitions on both the SSD and HDD to allow as much space as you want for Ubuntu. Next, install Ubuntu and choose the "something else" option when prompted for installation method. Click to add new partition for / which will be on the free space on your SSD, then likewise for /home on the HDD.

When you've finished installing you should get a Grub screen during boot where you can choose Win or Ubuntu. Edit your /etc/fstab as root to add the noatime,discard option as above. Your Ubuntu will seem incredibly responsive when running off your SSD. Enjoy :)

---

### Post by Nardon on 2012-08-13
Alright thanks a lot for the help! Will start installing right away. :D

---

### Post by Lupajz on 2012-08-13
Maybe some usefull tricks : 
> [http://wiki.debian.org/SSDoptimization](http://wiki.debian.org/SSDoptimization)

---

