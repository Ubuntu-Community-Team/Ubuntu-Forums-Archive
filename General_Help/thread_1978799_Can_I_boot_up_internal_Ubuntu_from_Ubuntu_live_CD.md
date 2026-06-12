---
title: "Can I boot up internal Ubuntu from Ubuntu live CD?"
date: 2012-05-12
forum: General Help
---

### Post by dragonfly41 on 2012-05-12
My usual Ubuntu 10.10 configuration has hit a problem 

desktop freezing .. then after REISUB forced reboot ..

> file system check or mount failed
disk drives are being checked for errors
disk 1 of 1 (0% complete)

But I cannot get beyond that if I press F to fix the errors.

I think this is due to some bad sectors on the disk which is about ready to be retired .. although Vista still boots up o.k. in dual boot mode where the bad sectors are in two Windows ntfs partitions.   

My old disk has shown bad sectors in partitions in GParted for some time but still chugs along.   

I do have a backup image but it is out of date and this is a warning for me to act to bring my backup up to date.

And I'll setup more frequent backups.   Meanwhile ..

...

I booted up into Ubuntu live CD 10.10 session.

and in Places I could see all the partitions.  In case it is needed I attach in RESULTS.txt the results of running bootinfoscript.

I can mount and inspect the internal Ubuntu partitions (root and home) which do not boot up.
/dev/sda7    root partition
/dev/sda8    home partition

...

[COLOR=Blue]**Now to my question ..**[/COLOR]

I vaguely remember reading somewhere in this forum that while running the Ubuntu live CD session
it is possible to boot up into the Ubuntu OS in file system ..

i.e. to switch from Ubuntu live CD running session into installed Ubuntu session.

Is this possible ... and if so how do I do this from terminal command in Ubuntu live CD?

---

### Post by jadtech on 2012-05-12
if the HD has known issues it is possible it has retired its self not waiting :) 

you can mount  the partitions from live cd no problem  you can scan them even copy and remove files and such  you need dont want to lose  not sure you can boot them  that way  ..

---

### Post by dragonfly41 on 2012-05-12
Thanks .. I do know that I can work on the mounted file system and copy to external USB drive .. but my question was quite different .. can I in any way _**[COLOR=DimGray]launch[/COLOR]**_ Ubuntu in the file system to take over from the Ubuntu live CD session?   More out of curiosity than necessity.

And the disk hasn't quite reached retirement age.

---

