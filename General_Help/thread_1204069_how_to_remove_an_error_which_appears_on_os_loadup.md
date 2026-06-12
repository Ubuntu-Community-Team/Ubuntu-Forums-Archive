---
title: "how to remove an error which appears on os loadup"
date: 2009-07-04
forum: General Help
---

### Post by rohanhimanshusingh on 2009-07-04
I've a hard drive partiton called work ntfs.. 

on boot up I get a dialogue saying 

Could not find "/media/work" 
"Please check the spelling and try again" 
 ok

/////

please tell me how do I remove this error from appearin everytime i boot up.

pretty annoying...
[:)]


thnx

---

### Post by TeoBigusGeekus on 2009-07-04
When you mount the drive, where is it mounted?
Also, post us the contents of the /etc/fstab file.

---

### Post by rohanhimanshusingh on 2009-07-09
I have 3 ntfs partitions...

I get that error dialogue when ubuntu has fully started.. I just need to click Ok and it goes...
when I remove the password authentication and  restart ubuntu... next time the error goes and what I get is ... A file browser opens that partition..... thats means something is just trying to open that partition.... thats all ... I searched auto start 4 anything thats trying to access that hard drive -... but nothing...


My Partition is mounted on "media/os%work" and I thing its sda3 ..
 my ext4 ubuntu partitions is on sda8 I guess

heres the etc/fstab  

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=83faa0d3-f379-44a4-84b6-33367fb8ba96 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=7fdf7386-402f-491a-ae3e-2360339a21dd none            swap    sw              0       0


Thanks

---

### Post by rohanhimanshusingh on 2009-07-25
hello... i still need help.... also wan2 add that if i take backup with remastersys and mount the iso on usb flash drive .. then boot from the usb flash... there is no error on that... and works as good as my system... 

is there any workaround

---

