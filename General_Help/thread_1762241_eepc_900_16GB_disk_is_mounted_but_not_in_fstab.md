---
title: "eepc 900 16GB disk is mounted but not in fstab"
date: 2011-05-18
forum: General Help
---

### Post by newairly on 2011-05-18
ASUS eeepc900 Easy Peasy 1.6 (Ubuntu 10.04)

After I boot the 16GB second SSD disk is mounted as HOME on /media This seems to be a default.
However there is no entry in /etc/fstab to do this. How does it happen?

I want to move my home directories  to be on the 16GB disk so I need it to be mounted on /home rather than where it is by default which is /media/HOME
What do I have to do?

Phil

---

### Post by wildmanne39 on 2011-05-19
> **newairly said:**
> ASUS eeepc900 Easy Peasy 1.6 (Ubuntu 10.04)

After I boot the 16GB second SSD disk is mounted as HOME on /media This seems to be a default.
However there is no entry in /etc/fstab to do this. How does it happen?

I want to move my home directories  to be on the 16GB disk so I need it to be mounted on /home rather than where it is by default which is /media/HOME
What do I have to do?

PhilHi, is this as sd card,if so they are mounted in media as default I am not sure that can be changed. I know the commands to edit the fstab but I am not sure it is safe, hopefully someone who as tried it will answer also.

---

### Post by Irihapeti on 2011-05-19
I have an EeePC 900 with Ubuntu 10.04 on it, and my home directory on the second internal (SSD) drive.

To use the 16GB drive as your home directory you need to edit /etc/fstab. You need to do that as root (e.g. gksu gedit /etc/fstab or sudo nano /etc/fstab)

Here's what mine looks like:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

UUID=xxxxx /               ext2    errors=remount-ro 0       1
UUID=yyyyy /home		ext2	defaults	0    2


```

Replace the xxxx and yyyy with the UUID of your drives. To find out that, run the command
```
sudo blkid
```

You should then be able to transfer your home directory to the new location. Then you can delete it from the small drive, but it pays to make sure everything is working first. :)

---

### Post by newairly on 2011-05-21
Thanks everybody. I finally got it right. /home is now on the 16GB internal disk so I have plenty of room.

Phil
[URL="http://ubuntuforums.org/member.php?u=346442"]
[/URL]

---

