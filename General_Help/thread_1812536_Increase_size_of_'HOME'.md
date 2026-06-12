---
title: "Increase size of 'HOME'"
date: 2011-07-26
forum: General Help
---

### Post by love_linux1 on 2011-07-26
[COLOR="Red"]**[SIZE="3"]how to increase size of home[/SIZE]**[/COLOR]

I have installed ubuntu 11.04 on dual boot with XP. And partions for installation are following:

500GB: WIN 7 and other partions
80GB: XP[40GB] and Ubuntu[40GB]

For Ubuntu:
1) 33GB : system installation [ext4]
2) 500MB : /boot [ext4]
3) 2GB : linux_swap [ext4]
4) 250MB : /tmp [ext4]
5) 250MB : /home [ext4] 
6) 4GB : Fat32/windows

Ubuntu installed, there's no problem.

Now I need to increase the size of '/home' to 2GB. HOW TO DO THIS? Please help.

Thank you.

---

### Post by bodhi.zazen on 2011-07-26
> **love_linux1 said:**
> [COLOR="Red"]**[SIZE="3"]how to increase size of home[/SIZE]**[/COLOR]

I have installed ubuntu 11.04 on dual boot with XP. And partions for installation are following:

500GB: WIN 7 and other partions
80GB: XP[40GB] and Ubuntu[40GB]

For Ubuntu:
1) 33GB : system installation [ext4]
2) 500MB : /boot [ext4]
3) 2GB : linux_swap [ext4]
4) 250MB : /tmp [ext4]
5) 250MB : /home [ext4] 
6) 4GB : Fat32/windows

Ubuntu installed, there's no problem.

Now I need to increase the size of '/home' to 2GB. HOW TO DO THIS? Please help.

Thank you.

You can do this in several ways, easiest is to boot a live CD and use gparted.

You will likely have to resize your partitions in several steps, shrink a partition, apply changes, increase another partition, apply changes.

[http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C](http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C)

---

### Post by 3Miro on 2011-07-26
Gparted will let you move and resize partitions, however, MAKE SURE TO BACKUP ALL IMPORTANT DATA FROM YOUR HDD. If something goes wrong, you can lose everything.

---

### Post by love_linux1 on 2011-07-26
can't i do this without live cd. I mean just use gparted from ubuntu os.

---

### Post by bodhi.zazen on 2011-07-26
> **love_linux1 said:**
> can't i do this without live cd. I mean just use gparted from ubuntu os.

No, you can not resize a partition while is it in use.

The live CD is easiest, if you insist you can boot Ubuntu to recovery mode, unmount /home, and use parted from the command line.

---

### Post by love_linux1 on 2011-07-26
ok.. Let me try it. Thank you everyone.

---

### Post by CatKiller on 2011-07-26
Just for info, you probably don't need a /boot partition, and even if you did it only needs to be tiny, like 64MiB or so. You don't need a /tmp partition either. You probably won't need 33GiB for everything but /home - 15 GiB or so could easily go for files in your Home folder, but since you have a bunch of other partitions you probably aren't planning on putting music or pictures or whatever there anyway.

---

### Post by ajgreeny on 2011-07-26
> **love_linux1 said:**
> [COLOR=Red]**[SIZE=3]how to increase size of home[/SIZE]**[/COLOR]

I have installed ubuntu 11.04 on dual boot with XP. And partions for installation are following:

500GB: WIN 7 and other partions
80GB: XP[40GB] and Ubuntu[40GB]

For Ubuntu:
1) 33GB : system installation [ext4]
2) 500MB : /boot [ext4]
3) 2GB : linux_swap [ext4]
4) 250MB : /tmp [ext4]
5) 250MB : /home [ext4] 
6) 4GB : Fat32/windows

Ubuntu installed, there's no problem.

Now I need to increase the size of '/home' to 2GB. HOW TO DO THIS? Please help.

Thank you.
Why on earth have you made life so difficult with this complicated partition setup?  Separate partitions for /boot and /tmp are not necessary, and make things more difficult, and with only 250MB for /home in particular, and the same for /tmp I imagine you might easily run out of space some times.

Where do all your data files go?  They are normally in /home, in there own folders, Documents, Music, Videos, etc etc, so 250MB is nowhere near enough for most users of a computer.  Some people make use of a separate disk, shared between the two OSs, formatted as ntfs, and put all their data fgiles there, but you make no mention of a similar system.

If your data files do not go somewhere which you did not mention in your post, I would be sorely tempted to start again and install Ubuntu afresh with just a /, ie your system partition of about 10GB, and a separate /home partition of the rest, except for the 2GB swap.

---

### Post by ddastoor on 2011-07-26
> **bodhi.zazen said:**
> You can do this in several ways, easiest is to boot a live CD and use gparted.

You will likely have to resize your partitions in several steps, shrink a partition, apply changes, increase another partition, apply changes.

[http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C](http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C)

one word of caution here: i recently learnt myself (in a post here) that IF the ext3 (inthis case /home) partition and a windows partition is contiguous, as in side by side, then u should NOT just shrink the windows one, thus increasing the ext one as u might lose data in the windows one,,

the proposed way would be:
first use a fancy windows partition manager, and from windows shrink the windows one, then boot into linux and then use gparted to then increase the /homr partition... 

this is if the linux and windows partitions are side by side..

---

### Post by s3a on 2011-07-26
> **bodhi.zazen said:**
> No, you can not resize a partition while is it in use.

The live CD is easiest, if you insist you can boot Ubuntu to recovery mode, unmount /home, and use parted from the command line.

It is possible to increase the size of a partition while it is mounted if you use LVM which I believe needs the alternate installer. To my knowledge, you cannot reduce the size of a partition while it is mounted but basically, you leave a bunch of hard drive space unallocated and then increase the size of the partition of your choice. This is useful mostly for servers and I really don't think the OP wants something more complicated than the usual partitioning mechanism but I am saying just in case it interests anyone.

---

### Post by bodhi.zazen on 2011-07-26
> **ddastoor said:**
> one word of caution here: i recently learnt myself (in a post here) that IF the ext3 (inthis case /home) partition and a windows partition is contiguous, as in side by side, then u should NOT just shrink the windows one, thus increasing the ext one as u might lose data in the windows one,,

the proposed way would be:
first use a fancy windows partition manager, and from windows shrink the windows one, then boot into linux and then use gparted to then increase the /homr partition... 

this is if the linux and windows partitions are side by side..

Data loss can always occur when you resize, you should back up first. I doubt it had to do with the geometry of your disk.

> **s3a said:**
> It is possible to increase the size of a partition while it is mounted if you use LVM which I believe needs the alternate installer. To my knowledge, you cannot reduce the size of a partition while it is mounted but basically, you leave a bunch of hard drive space unallocated and then increase the size of the partition of your choice. This is useful mostly for servers and I really don't think the OP wants something more complicated than the usual partitioning mechanism but I am saying just in case it interests anyone.

As you say, LVM is a bit off topic on this thread ;)

---

