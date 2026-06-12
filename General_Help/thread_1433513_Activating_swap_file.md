---
title: "Activating swap file"
date: 2010-03-19
forum: General Help
---

### Post by vksingh on 2010-03-19
Hi,

I am using ubuntu 9.04 on my laptop from past 8 months. These days when I boot my laptop, The booting process takes more time on the following step:

**Activating swap file**

Please help.


Thanks,

Vivek

---

### Post by Naiki Muliaina on 2010-03-19
I had a similar problem long time ago. I believe i went into /etc/fstab and commented a relevant section of fstab.

---

### Post by vksingh on 2010-03-19
**My details of /etc/fstab file**

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=4edb9e9f-b29d-45b5-be86-f43c88812731 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e131efb1-6b75-44f6-9812-5071e3cf0a5d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
~                                                                               
~                                                     



If any change have to done, please let me know.

Thanks,

Vivek

---

### Post by wojox on 2010-03-19
Does it actually activate Swap? What does this command return:

```
free -m
```

---

### Post by john newbuntu on 2010-03-19
Run the command "sudo blkid" and make sure that the UUID for the swap device matches the UUID in the /etc/fstab file for swap.  If not, change the UUID in fstab and reboot.
Also run "sudo swapon -a" and "sudo swapon -s" to see swap usage summary.

---

### Post by anaconda on 2010-03-19
actually
it would be better to address swap-partition with (line in fstab) 
/dev/sda6 none swap sw 0 0
instead of the 
UUID=e131efb1-6b75-44f6-9812-5071e3cf0a5d none swap sw 0 0

And why?
because the UUID of your swap-partition changes every time it is formatted. (eg. when installing a different version of ubuntu (or any linux) to another partition or another hard-disk.

the /dev/sda6 address stays the same even after re.formatting the swap-partition.

---

### Post by Enigmapond on 2010-03-19
In actuality, if you have sufficient RAM, the swap isn't even needed in fact, it will slow things down as well as taking up needless space. It's harder to read than RAM. I have 750mb of RAM and I adjusted the swapness to 10...now, the swap isn't even utilized and the computer runs just great and never goes above about 57% of RAM.

---

