---
title: "How change mount point?"
date: 2011-05-31
forum: General Help
---

### Post by silka on 2011-05-31
Hello, I need your help to change mount point :)

When I installed ubuntu, i was using this system:


[LIST]
[*]32 GB for ext4 format  "/" mount point
[*]288 GB was not formated NTFS file system partition (here was the second D:\ windows partition)
[/LIST]

Now I have copied all files what I need to home folder and now I want to change my 288 GB partition to the /home mount point. By the way, I have already formated this partition to ext4. So I want to make this HDD system:


[LIST]
[*] 32 GB         ext4 format       "/" mount point
[*] 288 GB       ext4 format      "/home" mount point
[/LIST]

---

### Post by silka on 2011-05-31
anyone?

I tried add /home mount point using fstab, but after restart I have an error and all panels were gone...

look to my fstab maybe here is some problem?

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=a8225b3a-241b-4202-a63c-d6bc33611021 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=dcd47510-81c4-4f38-8310-835801ac2a1d none            swap    sw              0       0
# home partition
#UUID=8a3181cb-ff2c-42d0-b7cc-ff699924d22a  /home          ext4    defaults    0       0
```

---

### Post by searchfgold6789 on 2011-05-31
Make sure that you have all of the user data copied there (e.g. /home/you; home/root) instead of just the contents of /home/you.

---

### Post by silka on 2011-05-31
I just find guide how to change mount point.

[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

---

