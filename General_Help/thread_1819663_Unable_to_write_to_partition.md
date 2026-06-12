---
title: "Unable to write to partition"
date: 2011-08-06
forum: General Help
---

### Post by doc_cypher on 2011-08-06
HI

I recently installed ubuntu 11.04. After installation, I created two ext4 partitions in my hard drive. My problem is that I can't create any files in these partitions.  These partitions are not automatically mounted at boot time, but once I try to access them , they get mounted. I thought all this was managed by /etc/fstab file but I can't see any entry for these partitions there.
So, I created an entry for both these partitions in fstab file with the following options: auto,user,exec,rw,suid,dev
However, now when i boot, i see that there are two partitions already mounted as earlier and there are two more in the Places menu. I am not able to mount them since they are already mounted. And I still can't create any files in those partitions.
How do I fix all this?

---

### Post by oldfred on 2011-08-06
Welcome to the forums.

Post your fstab.
gksudo gedit /etc/fstab

If you run this does it give any errors, you should run it after any edits of fstab to make sure you can reboot.

sudo mount -a

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by doc_cypher on 2011-08-06
Thanks for the reply. Here is my fstab file. The last two commented out lines are the ones I had added.

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=458845e7-2083-43cc-b623-b110f6f84c40 none            swap    sw              0       0
## Added by self
#UUID=2d62867e-0c82-4b53-95e1-7eac1dfb5ea0 /media/Documents ext4 auto,user,exec,rw,suid,dev 0 2
#UUID=fe0b7a33-a254-408a-bab0-a24b4f7de65b /media/Multimedia ext4 auto,user,exec,rw,suid,dev 0 2

```Also, here is the output from "sudo fdisk -l"

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003930e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20971520   83  Linux
/dev/sda2           14464       14594     1044481    5  Extended
/dev/sda3            2611        6528    31457280   83  Linux
/dev/sda4            6528       14464    63745024   83  Linux
/dev/sda5           14464       14594     1044480   82  Linux swap / Solaris

```sda1 is my root partition. sda3 and sda4 are the ones I created by shrinking sda1.

---

### Post by doc_cypher on 2011-08-06
I got this solved. I just had to do a chmod 777 on my mount directories.
I also changed the "user" option to "nouser" in fstab. Now I don't get duplicate entries in my Places menu. 
But I am not sure what was the problem with the "user" option.

---

### Post by blind2314 on 2011-08-07
> **doc_cypher said:**
> I got this solved. I just had to do a chmod 777 on my mount directories.
I also changed the "user" option to "nouser" in fstab. Now I don't get duplicate entries in my Places menu. 
But I am not sure what was the problem with the "user" option.

That does leave your partitions wide open to everyone, with full permissions (in case you didn't realize). There are better ways to fix the problems you were having, but if you're happy with this solution, that's your choice. If so, mark the thread as solved please.

---

### Post by doc_cypher on 2011-08-07
I do realize and I am happy with this solution. Those partitions are just ways to organize my data, and they can be accessible to everyone.
What are the better ways to do this, apart from doing a chmod? Also, sorry to ask , but how do I mark this as solved.

---

### Post by bodhi.zazen on 2011-08-07
> **doc_cypher said:**
> I do realize and I am happy with this solution. Those partitions are just ways to organize my data, and they can be accessible to everyone.
What are the better ways to do this, apart from doing a chmod? Also, sorry to ask , but how do I mark this as solved.

There is nothing wrong with having shared data that is readable by all , if that is the nature of your data.

Private data obviously would be another matter.

You should be able to mark this thread as solved under thread tools.

---

