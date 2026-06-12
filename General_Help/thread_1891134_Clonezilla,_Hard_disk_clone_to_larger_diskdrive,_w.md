---
title: "Clonezilla, Hard disk clone to larger diskdrive, windows will not boot"
date: 2011-12-04
forum: General Help
---

### Post by lindsay7 on 2011-12-04
I used Clonezilla to clone a 500gig drive to a 1000gig drive. My original 500gig drive had Ubunto 10.4, windows 7, a data partition and Ubuntu 11.10 on it. The clone looks like it has all the partitions on it and I can boot to either Unbuntu partitions but I can not get the windows 7 partition to boot, I have tried to use Testdisk and Grub-fix and worked on the ntfsfix et, but nothing works, here is the location of the boot script. [http://paste.ubuntu.com/760066](http://paste.ubuntu.com/760066). Does anyone know what I can do to fix this problem.

Thank you.

---

### Post by Mark Phelps on 2011-12-05
Did you resize the partitions during the clone operation? OR did you leave them the original sizes?

Asking because even Windows cloning apps can have problems if you resize the partitions during the cloning.

To try to get Windows booting again, look into Boot-Repair:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by lindsay7 on 2011-12-05
Thanks for the response Mark,  I did resize the partitions using Clonezilla and I have tried using the Boot-Repair software. Windows will still not start up. If I format the Windows partition is there another way to get my windows OS on the patition from original 500gig disk that has two versions of Ubuntu on it plus the Windows 7 os.

Thanks for your help.

---

### Post by Mark Phelps on 2011-12-05
The only success I've had in "cloning" a drive containing multiple filesystems to another drive is when I did not do a resize in the process.

That can involve a lot of post-cloning partitioning work, if you then want to resize partitions, but I've found it tends to work better.

---

### Post by lindsay7 on 2011-12-05
Thanks for the good advice,Clonzilla does not say much about this in their docs.

---

### Post by Mark Phelps on 2011-12-05
If you're willing to experiment, you can also try the FREE cloning solutions from Macrium Reflect, EASEUS Partition Master, and Partition Wizard.  These are all Windows apps -- and while they will most probably clone the Windows partitions OK, I have no idea if they will clone the Linux partitions as well.

But, AFAIK, they are all free, so it's worth trying -- especially if one of them ends up working.

---

### Post by coffeecat on 2011-12-05
> **lindsay7 said:**
> If I format the Windows partition is there another way to get my windows OS on the patition from original 500gig disk that has two versions of Ubuntu on it plus the Windows 7 os.

This following *should* work, but no 100% guarantee.

Put the original 500GB drive back in the machine and ensure that you can boot Windows. Now install Macrium Reflect Free.

[http://www.macrium.com/reflectfree.aspx](http://www.macrium.com/reflectfree.aspx)

Create a bootable Macrium rescue CD (Linux based!) and also create an image of your C: partition using Macrium, writing it to an external drive. Now put the new 1000GB drive in and reformat the partition you want to clone Windows onto. (This may not be necessary - Macrium may be able to write over the partition's filesystem - but it won't do any harm.)

Now boot up with the Macrium CD and restore your image on the external drive onto your new partition. Macrium cannot restore to a partition smaller than the original, but I'm fairly sure it will restore to a larger one. If not, let it make the restored partition the same size as the original and then you can enlarge the C: partition from inside Windows once it is booting successfully from your 1000GB drive.

---

### Post by lindsay7 on 2011-12-05
Thank you both for the info on refectfree, I will give it a try. I only use windows for quicken and turbotax and I have other computers that I can use for those, so if I can not get this clone disk to work, it is no big loss. I will just end up with a larger dirve for my two Ubunto partitions, I may just use the other partition for another Linux distro.

Thanks again for the help.

---

