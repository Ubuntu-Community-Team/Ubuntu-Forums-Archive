---
title: "making root bigger"
date: 2006-02-28
forum: General Help
---

### Post by issueperson on 2006-02-28
my root partition isn't big enough.
i have 15 gigs of unformatted harddrive space.
if i wanted to make / an 8 gig partition, could i format off an 8 segment, copy everything from root to it, and rename it or remount it somehow, then remove the other partition?
someone tell me exactly how i'd want to do that?

thanks,
brady

---

### Post by K.Mandla on 2006-02-28
If you just want to resize that partition, you might try the GPartEd tool, which you can install via Applications > Add Applications. It's under System Tools. It works a lot like Partition Magic, if you've ever seen that.

Edit: Now that I think about it, you might not be able to resize your active partition. But I haven't used that in a while, so you might try it.

---

### Post by issueperson on 2006-02-28
unfortunately, my root and free space are not side-by-side, so if i resized it, it'd overwrite another partition.
thanks for the idea though.

---

### Post by dcstar on 2006-02-28
[QUOTE=K.Mandla]If you just want to resize that partition, you might try the GPartEd tool, which you can install via Applications > Add Applications. It's under System Tools. It works a lot like Partition Magic, if you've ever seen that.

Edit: Now that I think about it, you might not be able to resize your active partition. But I haven't used that in a while, so you might try it.[/QUOTE]
You can find boot CD images with these tools on them, they work well:

[http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html)
[http://www.sysresccd.org/Index.en.php](http://www.sysresccd.org/Index.en.php)

---

### Post by cotcot on 2006-02-28
How is your partition table ? (can you post the output of "sudo fdisk -l" ?)

You can change (move and resize) partition with a GParted or QTParted from a liveCD. These are GUI for GNU Parted. GNU Parted has a good manual : [http://www.gnu.org/software/parted/manual/html_mono/parted.html](http://www.gnu.org/software/parted/manual/html_mono/parted.html)
Resizing is only possible from the end. If you want the starting point of a partition to be changed first move.

---

### Post by issueperson on 2006-02-28
my partition table is a bit messy, 'cause i used to triple-boot windows, slackware, and ubuntu.  i ditched slackware when they ditched gnome.  KDE makes me sad.

right now, my partition table is:
---------------------------------------------------------
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        3992    32001480    7  HPFS/NTFS
/dev/sda3            5712        9729    32274585    5  Extended
/dev/sda4            3993        5037     8393962+  83  Linux
/dev/sda5            9487        9729     1951897+  83  Linux
/dev/sda6            9364        9485      979933+  82  Linux swap / Solaris
/dev/sda7            6931        9362    19535008+  83  Linux
/dev/sda8            6322        6929     4883728+  83  Linux
/dev/sda9            5713        6320     4883728+  83  Linux
----------------------------------------------------------

where **/dev/sda4** is my blank partition that i want to change to root.  i have it mounted as **/root2**.  /dev/sda5 is root, and then 7-9 are /etc /home and /opt (in no particular order).

so i'm wondering, can i just copy /sda5 to /sda4, and then change it to boot as /  ?

also, how would i need to alter my fstab if i did that?  right now it looks like:
-------------------------------------------------------------------------
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /home           ext3    defaults        0       2
#/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/sda2       /media/windows    ntfs    nls=utf8,umask=0222 0 0
/dev/sda9       /opt            ext3    defaults        0       2
/dev/sda8       /usr            ext3    defaults        0       2
/dev/sda4       /root2            ext3    defaults        0       2
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
-----------------------------------------------------------------
could i just change the /dev/sda5 section to /dev/sda4 (the one i want to boot as root)?
i don't want to do too much trial-and-error with this, 'cause if i screw it up i might have to start everything over.

thanks to anyone who can help.

---

### Post by issueperson on 2006-02-28
i tried to copy it, and when it's in use, i don't think it's gonna work.
so anyone have any ideas?  i'm stuck but i don't want to reinstall it and lose everything.

help!

---

### Post by bluegene on 2006-06-12
there is nothing to be afraid of just make sure u back up ur data b4 u proceed..

---

