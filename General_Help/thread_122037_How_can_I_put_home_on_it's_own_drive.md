---
title: "How can I put /home on it's own drive?"
date: 2006-01-26
forum: General Help
---

### Post by Daminator on 2006-01-26
I installed Ubuntu, dual boot, on my laptop using the default drive partitions.

I'm not thinking (how many of you agree?) that the /home partition should have it's own drive to make things easier for fresh installs.

I've seen that some people have a separate partition for apps too, but I'm less sure of how helpful that is (would the system know that you had the apps installed if you did a fresh OS install? Or is that me with my old windows head on? Would you need to manually re-do all menu short cuts?)

I'm interested on thoughts on these issues, but also interested how in the world I go about doing it if I decide to do one or both of the above options.

Cheers

---

### Post by Stereotypical Rage on 2006-01-26
I use just /home on a partition on my main hdd.

I set mine up upon install though. I assume you could do something with it now, in the fstab (File System Tab.)

Now when I upgrade Ubuntu releases, I just format /(root) and my home I don't touch. It's pretty sweet.

---

### Post by Robor on 2006-01-26
[QUOTE=Stereotypical Rage]I use just /home on a partition on my main hdd.

I set mine up upon install though. I assume you could do something with it now, in the fstab (File System Tab.)

Now when I upgrade Ubuntu releases, I just format /(root) and my home I don't touch. It's pretty sweet.[/QUOTE]
I'm a noob to Linux/Ubuntu and I did the same thing with mine because it was recommended.  I have a question though, what is the advantage?  Or should I ask, what is preserved that would've normally been lost?  I would assume that on the next release we'll still have to re-install all programs that aren't loaded by default, right?

---

### Post by aysiu on 2006-01-26
Having a separate /home partition is a great idea.
I know some people have had no troubles with dist-upgrading from Hoary (5.04) to Breezy (5.11), but I (and many others) had weird issues crop up (damaged X or locale settings). You can almost never lose with a clean installation of the newest Ubuntu version... unless you accidentally install it on the wrong partition!

---

### Post by Daminator on 2006-01-26
So how do you do it?
Should I massage space with Gparted?
How should I format the new /home drive?
How should I move the files?
Then once everything's moved around, should I used Gparted again to reduce space on the boot drive? (making more room for the new /home drive)?

And what about the idea of having apps on a seperate drive? I don't see the point of that myself unless it's just to make the boot drive it's self very small.

---

### Post by dcstar on 2006-01-26
[QUOTE=Daminator]
........
And what about the idea of having apps on a separate drive? I don't see the point of that myself unless it's just to make the boot drive it's self very small.[/QUOTE]
You separate static and dynamic files for performance and/or security reasons.

If the Ubuntu program and system files are on a separate drive/filesystem, then it is likely that there won't be too many "writes" to that filesystem, so (in theory) there is less likelihood of corruption etc. than with a filesystem containing user's home directories (that can have a lot of R/W activity).

Having them on separate drives means that they can operate independently of each other, and the system does not have to wait for one drive to do the work of accessing programs and also working with user files.

In high performance Unix systems, the Swap space is usually on a separate drive(s).

---

### Post by TecSoft on 2006-01-26
[QUOTE=Daminator]I installed Ubuntu, dual boot, on my laptop using the default drive partitions.

I'm not thinking (how many of you agree?) that the /home partition should have it's own drive to make things easier for fresh installs.

I've seen that some people have a separate partition for apps too, but I'm less sure of how helpful that is (would the system know that you had the apps installed if you did a fresh OS install? Or is that me with my old windows head on? Would you need to manually re-do all menu short cuts?)

I'm interested on thoughts on these issues, but also interested how in the world I go about doing it if I decide to do one or both of the above options.

Cheers[/QUOTE]
You can do this when you are installing. When you are making partions make a partion for /home dir. Instead of choosing root (/) choose /home. This will install the home directory on its own partion. You can do this with other drives. Just create a partion and set it to the /home dir.

---

### Post by mettallicat on 2006-01-26
look 

```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /home           ext3    defaults        0       2
/dev/hdb1       /media/data     xfs     defaults        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



```

is that what you want?

---

### Post by Daminator on 2006-01-28
I can understand that, it's how to get there I'm not too sure about.
I'm guessing that I make the /home drive with gparted first, but then what order should I do things?
Tell ubuntu to use this new drive as 'home' and then move all of the files across? Or move the files across and then tell ubuntu about the change? What's the best way to go about it?

---

### Post by Rumpty on 2006-01-28
Have a look at this article - it should help.

[http://www-128.ibm.com/developerworks/linux/library/l-partplan.html](http://www-128.ibm.com/developerworks/linux/library/l-partplan.html)

---

### Post by MountainX on 2008-02-26
> **Daminator said:**
> 

I've seen that some people have a separate partition for apps too ...would the system know that you had the apps installed if you did a fresh OS install? Or is that me with my old windows head on? Would you need to manually re-do all menu short cuts?

I

I'm interested in the answer to this too.

---

