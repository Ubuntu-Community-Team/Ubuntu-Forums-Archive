---
title: "Mount several partitions at same level in tree."
date: 2010-12-29
forum: General Help
---

### Post by bdemers on 2010-12-29
Let's see if I can explain.

I initially set up my filesystem on a single disk, normal, plain vanilla, with a partition for /var. 
 
Just as an example let's say I have in this file system a path /var/lib/temp.

Under /temp I want 4 directories /one, /two, /three, and /four so I get /var/lib/temp/one and /var/lib/temp/two, etc.  So I created them.

Now I want to separate the directories /one, /two, /three and /four such that each is on its own partition.  I create the four partitions and then copy into the appropriate partition /one, /two, /three, and /four.  Of course all the stuff inside of those directories are moved over as well.  

In fstab I locate a mount point called /var/lib/temp, located just below the /var mount point, and it is on the line with the partition that holds /one.

Save fstab, mount -a and it works.  

Back to fstab, add a second line below the first with same mount point but this time with the partition for /two.

Mount -a and /one fails and /two is up. 

Oh-oh!!!!!

So yes, I can't just put the fstab file together the way I did. I see that clear as day. Last line wins.  What I don't see is how to make it right.  :confused:

---

### Post by Norcalli on 2010-12-29
The way you described this is quite abstract for such a simple thing and I'm not sure I completely understand it, so I'm going to show you what I would do if I wanted to accomplish this, and tell me if that is what you have already tried.

```

# <fs>     <mnt>       <type>  <options>  <dump>  <pass>
/dev/sda   /var        ext4    defaults   0       1
/dev/sdb   /var/tmp/1  ext4    defaults   0       1
/dev/sdc   /var/tmp/2  ext4    defaults   0       1
/dev/sdd   /var/tmp/3  ext4    defaults   0       1

```

The order is important and you should make sure that the mount points actually exist.

---

### Post by nothingspecial on 2010-12-29
I could (probably) be talking rubbish here....... but


You have to mount each partition.

If you see what I mean.

EDIT **Like the above poster said**

---

### Post by bdemers on 2010-12-29
Here's a picture of my fstab.
You can see that /var is in the sda3 partition. sdb2 has a dir /101, sdb1 has /111, sdc2 has /121, and sdc1 has /131.  I verified by removing the rem's one at a time that they exist and mount individually just fine.  If I change my mount point to /var/lib/vz/private/101, /var/lib/vz/private/111, /var/lib/vz/private/121, /var/lib/vz/private/131 I fail mounting.

I am of the (mistaken???) opinion that the partition I am trying to get mounted has to have the /101, etc on it, not /101 as the mount point.  Isn't the mount point where the new partition is to be attached to?


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
/dev/sda4       /home           ext3    defaults        0       2
/dev/sda3       /var            ext3    defaults        0       2
/dev/sdb2       /var/lib/vz/private   ext3   defaults  0       2
# /dev/sdb1       /var/lib/vz/private   ext3   defaults  0       2
# /dev/sdc2       /var/lib/vz/private   ext3   defaults  0       2
# /dev/sdc1       /var/lib/vz/private   ext3   defaults  0       2
/dev/sda2       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by dandnsmith on 2010-12-29
No, your assumption is wrong.

You should mount the 101 at a point ../101
with whatever content you want to see in 101 as the top level in that directory, so there is no mention of 101 in the top level of the partition.

HTH

---

### Post by bdemers on 2010-12-29
Let me go give that a try, thanks

---

### Post by bdemers on 2010-12-29
Thank you for your correction.  I moved all my data up one level so that the /101 directory doesn't exist on the partition.  I established an empty directory of /101 under /private.  I added /101 to the mount point in fstab.  Did that procedure to all 4 of the targets.  Works just fine.

I have learned a lot here.  As you may be able to discern, this is my first go 'round with this procedure.  Mighty powerful stuff when you start considering the versitility in could provide.

Thanks, one more time

---

