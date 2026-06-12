---
title: "RAID 5 array problem"
date: 2011-08-31
forum: General Help
---

### Post by sumasage on 2011-08-31
I am trying to create a new RAID5 array with 4 drives.  I followed this guide to create the array. [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID)

Right after i used fdisk to create the partitions and set the partition type to "Linux RAID" on all 4 drives, Ubuntu auto created a RAID array call md127 with the four drives as its components.  I find this odd and disturbing, why would it does that?  I thought maybe there was some left over metadata on the 4 drives so i searched on how to delete the raid array and all metadata on the drive.  I found this guide [http://ubuntuforums.org/showthread.php?t=884556](http://ubuntuforums.org/showthread.php?t=884556) and deleted the md127 array and all the meta data.  I rebooted a few time to make sure the array doesnt show up again.

I then when through the entire process of creating the array again.  This time i named the array md5.  After the array fully synchronized i rebooted the machine.  When i turn the machine back on my the md5 array is gone.  The only RAID array i see in Disk Utility is an array call md127.  Looking at the components of md127 it has all the hard drives i used to create md5.  Interestingly the name of the array is still "5" as in md5.  See screenshot link below.

[[IMG]http://imageshare.web.id/images/g3yfjr1tk8a7ratcawy1_thumb.png[/IMG]]("http://imageshare.web.id/viewer.php?file=g3yfjr1tk8a7ratcawy1.png")[http://imageshare.web.id/images/g3yfjr1tk8a7ratcawy1.png](http://imageshare.web.id/images/g3yfjr1tk8a7ratcawy1.png)

md127 seem to be work just fine, i can mount it and everything.   My concern is that what happened to my md5 array?  why did the name changed to md127? Is this something new in 11.04?

---

