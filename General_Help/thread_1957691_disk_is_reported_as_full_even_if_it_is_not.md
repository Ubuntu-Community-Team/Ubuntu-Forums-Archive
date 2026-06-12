---
title: "disk is reported as full even if it is not"
date: 2012-04-12
forum: General Help
---

### Post by quickk on 2012-04-12
Hi everyone, 

   This is a strange one...

I am running kubuntu 11.10 on a first gen macbook air.   I've partitioned the drive in 3: maxos, /, and /home. 

For some reason, at some point over the last month or so, the free disk space reported on the / drive is zero:

```

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             8.9G  8.9G     0 100% /

```

It's also weird that my home partition does not show up.   

I've deleted 2GB worth of stuff on / (via the command line rm -rf, so it should not be in the trash), and the drive is still reported to be full.   I can't copy anything onto this drive, and it is messing up my whole system (no space for any temporary files).  

I've booted into mac OSX, and used a disk tool to visually view the space occupied by the files on /dev/sda2, and this tool reports that there is free space, yet I still can't copy anything onto this partition even in OSX.   

Any ideas of what is going on?

---

### Post by oldfred on 2012-04-12
Post your fstab to see if /home is there. And if it is do this to see if you get an error.

sudo mount -a
That remounts fstab to make sure you have no issues.

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by quickk on 2012-05-18
I tried your suggestions, and also a bunch of other things, to no avail.  Something must of been messed up with the drive itself because I couldn't even write to it from the mac side of things.   In the end, I took advantage of the fact that Ubuntu 12.04 was released and ended up just formatting my drive and reinstalling from scratch.   Everything now works great!   Thank you for the help.

---

