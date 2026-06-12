---
title: "End request i/o error during boot"
date: 2011-03-15
forum: General Help
---

### Post by Morimando on 2011-03-15
Hi there.
I've got a strange error here. During boot, the system posts serveral "end request i/o error /dev/sdb"-errors. 
I investigated the error but there is no sdb.
I have 4 drives running, 2 1TB drives, 1 500GB drive, 1 320GB drive.
The 500GB and the 320GB drive both have a 50GB partition merged into a striping raid of 100GB which is contains my root filesystem.
The others are storage and/or contain other Linux Distributions for testing as well as Windows 7. SMART-Data says that all drives are (more or less) fine.
I am however quite puzzled as to the whereabouts of sdb. My fstab mounts drives by UUID (since Ubuntu some time back developed the annoying habit of randomly assigning drive names (sdc becomes sdf often and vice versa).
Now the naming is as follows:
500GB (Samsung HD501LJ): sda
1TB (Seagate ST31000333AS): sdf
1TB (Hitachi HDS721010CLA332): sdg
320GB (Samsung HD321KJ): sdh
Tuxroot 107GB: md0 (RAID 0, in use, ready)
The Hitachi does contain some bad sectors (most likely from the time it was still residing within the external casing whose USB-Controller went AWOL, which is why I had to dismantle it and make the drive an internal one)

Does anyone have any idea from whence the error during the boot process stems? As the system runs as expected and does not suffer from slow response times, strange hard drive noise or the like, everything seems to be doing fine (physically), yet I'd very much like to get the problem solved or at least diagnosed before failure and/or data loss occurs.
TIA for any help :)

edit: The SMART Reports for Hitachi and Seagate drive have completed successfully (long test), the Samsung drives report that they've been cancelled, so I'll let them run again.

---

