---
title: "Recovering partition"
date: 2012-08-10
forum: General Help
---

### Post by txfiddler on 2012-08-10
I have an Iomega external network HDD.  In the process of deleting a folder that contained a little over 300 gigs of data it stopped functioning.  It would show up on the network but I would get an error message if I tried to open a folder.  I took the drive out of the case and ran the Seagate drive test on it and it came back as healthy.  I attached it to my Windows computer and it would show up in the disk manager but the file system on the partitions were not recognized.   After an initial Internet search I learned that it uses an XFS file system.   I attached it to my Ubuntu computer.  Three partitions showed up.  I could open the two smaller partitions but I could not open the main data partition.  I got the error.  “Unable to mount 996 GB file system.  Error mounting mount: mount: Structure needs cleaning”  If I go to the disk manager in Ubuntu, the drive shows up and lists three partitions.  The main data partition shows up as an XFS partition.  If I highlight the partition and run “check file system” it comes back as “file system is clean”.  If I try to mount the system, I get this error: “Error mounting volume...filesystem driver not installed.”  

I would appreciate any suggestions on how to possibly recover the data I have on that drive.

Thanks

---

### Post by dcstar on 2012-08-10
> **txfiddler said:**
> I have an Iomega external network HDD.  In the process of deleting a folder that contained a little over 300 gigs of data it stopped functioning.  It would show up on the network but I would get an error message if I tried to open a folder.  I took the drive out of the case and ran the Seagate drive test on it and it came back as healthy.  I attached it to my Windows computer and it would show up in the disk manager but the file system on the partitions were not recognized.   After an initial Internet search I learned that it uses an XFS file system.   I attached it to my Ubuntu computer.  Three partitions showed up.  I could open the two smaller partitions but I could not open the main data partition.  I got the error.  &#8220;Unable to mount 996 GB file system.  Error mounting mount: mount: Structure needs cleaning&#8221;  If I go to the disk manager in Ubuntu, the drive shows up and lists three partitions.  The main data partition shows up as an XFS partition.  If I highlight the partition and run &#8220;check file system&#8221; it comes back as &#8220;file system is clean&#8221;.  If I try to mount the system, I get this error: &#8220;Error mounting volume...filesystem driver not installed.&#8221;  

I would appreciate any suggestions on how to possibly recover the data I have on that drive.

Thanks

Install the **xfsprogs** package.

---

### Post by txfiddler on 2012-08-11
> **dcstar said:**
> Install the **xfsprogs** package.

OK I tried both xfs_check and xfs_repair.  I got "permission denied" each time.  Suggestions?
Thanks

---

