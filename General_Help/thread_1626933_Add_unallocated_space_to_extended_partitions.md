---
title: "Add unallocated space to extended partitions"
date: 2010-11-20
forum: General Help
---

### Post by Chethan S on 2010-11-20
I have the following disk partitions from the left side of partition table as of now:
  
[LIST=1]
[*]NTFS - Primary windows vista
[*]Extended - 3 Nos. all NTFS - middle one contains data
[*]Unallocated space
[*]NTFS - Primary
[*]NTFS - Primary HP Recovery
[/LIST]
  My intention is to add unallocated space to the extended partition. Will I be able to use Gparted to do it?
  

Or can I install Ubuntu in one of the extended partitions and make  this unallocated partition the home partition for Ubuntu. I am not able  to add new partition in this unallocated space as disk manager in vista  throws up an error no free disk space to complete the operation. I read  in some forum that OEM installations allow only 3 primary partitions and  one extended or 4 primary ones. Is it true for OEM's only or its a  universal rule?

---

### Post by mikewhatever on 2010-11-20
Since the extended partition is right next to the unallocated space, you should be able to enlarge the extended partition using Gparted. 
The four primary partition limit has nothing to do with OEM installations.
Once the unallocated space is added to the extended partition, you should be able to create more logical partition.

---

### Post by Chethan S on 2010-11-20
Thank you! This will solve my problem.

---

