---
title: "- Trouble Accessing a File Storage Partition/Drive -"
date: 2012-08-31
forum: General Help
---

### Post by Minty Freshness on 2012-08-31
:p Hi,

I think my computer is rebelling against me.

I made 3 partitions on my HD. One that boots ubuntu, one that boots linux mint and a third to store data. However, I am seemingly unable to access the third. They are labelled sda1, sda2 and sda6 respectively and are all formatted in ext3.

I made the third whithin an extended partition along with a partition for "swap space", which may have something to do with this.

*** the problem is that this third ext3 partition/drive does not show up in the devices column of the file browser. Although, I can access the file system (sda1) and sda2 (which is where I installed linux mint)

I typed "mount" into terminal which gave:

... /dev/sda6 on /data type ext3 (rw) ...

I also accessed the "fstab" file via "sudo getit /etc/fstab" which says:

... /data was on /dev/sda6 during installation...ext3...
and seems to suggest something like * mount point = 2 *


Help me maybe? [-o<

ok, here is the best copy I could get of my fstab:

# /etc/fstab: static file system information. 
# 
# Use 'blkid' to print the universally unique identifier for a 
# device; this may be used with UUID= as a more robust way to name devices 
# that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    nodev,noexec,nosuid 0       0 
# / was on /dev/sda1 during installation 
UUID=1e2ca52f-9db4-4101-b839-0330803d40cf /               ext3    errors=remount-ro 0       1 
# /data was on /dev/sda6 during installation 
UUID=e29c0307-b087-4266-8f7c-148b7aa9a672 /data           ext3    defaults        0       2 
# swap was on /dev/sda5 during installation 
UUID=cbe236ce-7103-4fa6-95db-b3930da74c04 none            swap    sw              0       0 
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by drmrgd on 2012-08-31
It might be helpful to see the whole contents of your fstab file.  Would you mind posting it here with the code tags so that we can see how the mount point is configured.

---

