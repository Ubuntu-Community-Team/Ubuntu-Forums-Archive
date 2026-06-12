---
title: "dd and cloning w/ubuntu"
date: 2012-09-25
forum: General Help
---

### Post by mperedithe on 2012-09-25
Hi everyone,  I'm repairing a windows based machine for my in-laws and the hard drive needs to be replaced.  The drive functions well enough to use dd or ddrescue, BUT I'm replacing their 1TB with a 500GB.  The data has the usual partitions for windows 7 and they have only taken up about 65GB with the OS and data.

What are the precautions for this type of cloning? Can I safely copy from a larger drive to a smaller one when the amount of data is so small?  Are there any arguments I can add to prevent problems (ie. rsync)?

Thanks for the help!

---

### Post by einonm on 2012-09-25
dd will copy the entire disk image verbatim quite happily, so you'll end up with a 500GB disk image on the 1TB disk.

I would perhaps suggest performing the dd, and then using GParted to increase the disk size, or even just add a new partition in the unused space if you prefer.

Just make sure if you're using dd, that the if= and of= devices are the correct way around!

---

### Post by mperedithe on 2012-09-25
Hi einonm,

Thanks for the quick reply.  But how about the other way round.  I need to copy the 1TB onto the 500GB.

---

### Post by Bobhuber on 2012-09-25
> **mperedithe said:**
> Hi einonm,

Thanks for the quick reply.  But how about the other way round.  I need to copy the 1TB onto the 500GB.
Fsarchiver will do what you want. It can be found on the System Rescue CD. I use it daily for backups and have restored more times than I care to mention.

[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

---

### Post by einonm on 2012-09-25
> **mperedithe said:**
> Hi einonm,

Thanks for the quick reply.  But how about the other way round.  I need to copy the 1TB onto the 500GB.

Oh yeah, sorry - I misread. :)

Just do it the other way around - Use GParted to reduce, and the dd to copy.

---

### Post by oldfred on 2012-09-25
Are you planning on having both drives continue to be connected? If so you will have issues of duplicate UUID.

dd is for same size to same size copying. It will not go larger to smaller. You may be able to shrink the large to the size of the smaller and have it work.

from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)

But do not use dd for copies from MBR to gpt partitioned drives
[https://wiki.archlinux.org/index.php/Disk_Cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)

Full image backup
GNU ddrescue (packaged as gddrescue, though once installed the command is "ddrescue") 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Many recommend clonzilla:
discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

---

### Post by mperedithe on 2012-09-25
Thanks for all the great suggestions!

The original hard drive needs to be replaced, so I won't be leaving it in the computer once the repairs are finished.  I was really hoping to not have to reload that crappy os and spend all that time getting drivers, updates, software, etc.  

Correct me if I'm wrong here but my understanding, at least with Windows XP, was that a change to the partition size always ended with an unbootable os.

---

### Post by mperedithe on 2012-09-25
After doing some research on Clonezilla and others, and with the suggestions posted here (thank you einonm and oldfred), I've decided to attack the problem as follows:

I'll use Gparted from ubuntu live cd to create a partition that matches the recovery partition from the original drive.

I'll use dd to copy the recovery partition.

Then, sigh, I'll use the recovery partition to reinstall the Windows os onto the new drive.

Thanks to everyone for their time and effort.

---

### Post by oldfred on 2012-09-25
Some more suggestions, if just Windows. 

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

