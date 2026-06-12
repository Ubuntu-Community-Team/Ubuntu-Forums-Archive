---
title: "restore ddrescue image"
date: 2011-02-01
forum: General Help
---

### Post by Skapunker on 2011-02-01
Hi

I've been using ddrescue to back up failing drives and it works great.  I want to be able to restore a good image to a new drive.  I tried ```
ddrescue image /dev/sda
``` but the partitions are not showing up after imaging to the drive, even though when I run a chkdsk repair on the drive Windows sees a Windows partition.  Gparted shows the filesystem a ntfs, but says the device /dev/sda1 doesn't exist.  The drive I'm trying to image is ntfs with Windows XP on it.  When I mount the image in Ubuntu it mounts fine and I can see the Windows files.

I'd appreciate the help on how to restore a ddrescue image file to a drive with Ubuntu, I'd really like to image drives this way rather than with other imaging software like I normally do

Thanks

---

### Post by Skapunker on 2011-02-01
Update:

I tried creating a new ntfs parition on the drive and then ```
ddrescue image /dev/sda1
``` and it gave me a write error at the end saying it ran out of space.  I'm trying to image back to the same drive so I guess having a parition already on there won't work since when I created the image I used ```
ddrescue /dev/sda image
``` I also tried mmls to see the partition and it says cannot determine partition type.  Anybody use ddrescue to copy a working Windows drive to a new one?

---

### Post by GailHard on 2011-04-02
Hi Skapunker: I have exactly the same problem - see here: [http://ubuntuforums.org/showthread.php?t=1715238](http://ubuntuforums.org/showthread.php?t=1715238)
 
In my case I restored the 200GB HDD (using ddrescue) to a new 500GB disk. Running testdisk , it sees the NTFS file system, lists its directories fine, but complains that the number of cylinders is different between fdisk and parted.
 
Windows "computer management -> Storage management" sees the disk, but does not assign it a volume or a drive letter.
 
Please update me if you have any progress; and I'll update you
 
Gail H

---

### Post by Skapunker on 2011-04-05
Gail H: I replied to you in your thread.

Update: I've used ddrescue several more times and doing what I originally did has worked fine, I think that drive just had more issues that I didn't have time to dig into.

---

