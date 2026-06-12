---
title: "XFS Parition Recovery - not sure where to put this post"
date: 2012-06-30
forum: General Help
---

### Post by Cpuboye11 on 2012-06-30
Good Day Gentlemen and Ladies. 

I've found my self in a bit of a pickle. One of my iomega 1tb nas drivers decided that the partition table was going to go ):P . I've stuck the drive in my machine and have concluded that either the drive formated it self clean or the partition table was lost or damaged. I'm not sure of which. 

Currently the partition was and still is a XFS partition. Just not data being used. I attempted to recover files using the photorec and test disk utility that you can download. Two problems with this:

1. It was recovering .zip and .rar files as regular folders. Meaning you tried open the file in one of the zip files and it wouldn't open. Error, file coupprted. 
2. It was going to take like 200 hrs. After two days of running non-stop. 

I've also tried xfs_repair with the selection - d and it was not able to fix the problem. Kept saying- sorry, could not find valid secondary superblock. 

If any suggestions could be given I would be very thankful. :popcorn:

Thank you,
Kyle

---

### Post by Cpuboye11 on 2012-07-02
I allowed photorec to finish, which took about 7 days in total... Non-of the data was usable in the sense of organization. 

Is there a way to rebuild a lost table. I know there is away to do it with DOS and NTFS. But XFS is just... Way different. :confused:

---

