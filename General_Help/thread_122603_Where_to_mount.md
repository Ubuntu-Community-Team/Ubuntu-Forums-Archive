---
title: "Where to mount?"
date: 2006-01-28
forum: General Help
---

### Post by Downtown on 2006-01-28
Ok, I figured out how to get both drives to read/write, after [this]("http://ubuntuforums.org/showthread.php?t=122523") problem.  But now I have a new problem.

My primary HDD (hda1) is set to mount on / while my secondary HDD (hdb1) is set to mount on /home/emilio/driveb

The problem is that /home/emilio/driveb is a part of / so when I move files from the primary drive to the secondary drive to make room on the primary, it doesn't show any additional free space, because technically, I'm still storing it in the primary drive.

Is there any way that I can mount and acess the secondary drive sperately from the primary the way if I put two drives in windows it recognizes them by two differnent letters?

---

### Post by akiro.yamamoto on 2006-01-28
Can you post your /etc/fstab file....??

---

### Post by akiro.yamamoto on 2006-01-28
Extra hard drives are normally mounted to media/ , well at least that's where I mount my extra hard drives.
Thsi is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               reiserfs notail          0       1
/dev/hdd2       /media/data     vfat    user,umask=000        0       0
/dev/hdd1       /media/extra    ntfs    user,ro,umask=0222        0       0
/dev/hdb1       /media/old-home ext3    defaults        0       2
#/dev/hda1       /media/win-xp   ntfs    defaults        0       0
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

As you can see I have 3 hard drives.
hda hdb and hdc.
The various partitions are mounted as I need them.
Now although the partition is mounted as part of the / heirachy it will not affect the space available to /. What you start with as the partition size for hda1 will remain the same unless you re-size that particular partition.
However the newly mounted Hard drive is avaiable for your use to store any files as needed. 
What this means is that /media/win_d is the same as D:\ in the windows world.
The fact that you have 100gb extra drive will not affect the partition that you install your OS to, so if that partition is 50gb and you install the 100gb hard drive, even in the wins world drive C will remain at 50gb not suddenly go to 150gb. In linux however you can specify the mount point for your extra hard drive. So if you plan on saving a lot of personal files or video but not change the amount of space the OS system itself will use you can mount the hard drive as your /home folder.

---

### Post by Downtown on 2006-01-28
Ok, sorry I didn't respond but I was testing different settings.  I've mounted hdb1 to /mnt/driveb as recommended in a tutorial I read and with the advice given here.  I moved around a lot of files to see the numbers and they're all making sense.  fstab is edited correctly to the best of my knowledge.  Thanks for your help.

---

