---
title: "USB devices affecting boot order and internal drive mounting"
date: 2010-08-06
forum: General Help
---

### Post by agarzon on 2010-08-06
I just switched from 8.10 to 10.04, and I am having a hard time with the way usb drives are mounting.

When I reboot the system, if the USB drives are connected, then Ubuntu reports a a problem in mounting my second internal hard drive. 

What's happening is that USB drives are getting the first drive names (sda, sdb etc) and the other drives, the internal ones, are following after. My standard fstab file looks like this:

```

  agarzon@euler:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e7466511-6709-4022-bb0c-af99601c048d /               ext4    errors=remount
-ro 0       1
# /home was on /dev/sda2 during installation
UUID=1a1392a9-68df-44ba-a607-66d5f788b4b7 /home           ext4    defaults      
  0       2
#adding the os back up partition
/dev/sdb1    /media/osBU   ext4    defaults     0        2
#adding the home back up partition
/dev/sdb2    /media/homeBU   ext4    defaults     0        2
agarzon@euler:~$ 


```

Where sdb1 and sdb2 are partitions on a second drive to back up my data from sda.

What do I need to do to get the usb drives mounted in a different way? Like mount only on sdd and up?

---

### Post by agarzon on 2010-08-06
Anyone? 
Also, I just realized that on my old system the internal hard drives were IDE, hence mounting as hda, hdb ...

Still, need some advice on this matter please....

---

### Post by agarzon on 2010-08-06
Bump...

---

### Post by agarzon on 2010-08-09
Wow, not a single reply... Anyone?

---

### Post by oldfred on 2010-08-09
I would change mount from drive to either UUID or label. Many prefer labels as they totally control those as even UUID's can change with major partition changes.

Understanding fstab
See section on using labels:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

