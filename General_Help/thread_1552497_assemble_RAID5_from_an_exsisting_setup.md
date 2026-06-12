---
title: "assemble RAID5 from an exsisting setup"
date: 2010-08-13
forum: General Help
---

### Post by hmblm1245 on 2010-08-13
I am have a WD Sharespace that has recently failed during a power outage. the drives all test good however the datavolume is missing. I can ssh into the device. What i am having trouble is (as a newbie) is reassbling the broken raid. after searching the WD forms and finding that someone posted 

at the prompt type: mdadm -D /dev/md2
You should get a message about it not existing.  If it does then this might not be the solution for you.
Then type: mdadm --assemble /dev/md2 /dev/sda4 /dev/sdb4 /dev/sdc4 /dev/sdd4
Then type: pvcreate /dev/md2
Then type: vgcreate lvmr /dev/md2
Then type: lvcreate -l 714329 lvmr -n lvm0


Trough Putty I managed to access the drive
login: root
pw: welc0me
 
- i get ASCI logo saying S6M-4MC
 
then I followed the guide:
mdadm -D /dev/md2
       --> mdadm: md device /dev/dev2 does not appear to be active.
mdadm --assemble /dev/md2 /dev/sda4 /dev/sdb4 /dev/sdc4 /dev/sdd4
       --> mdadm: dev/md2 assembled from 2 drives - not enough to start the array.
 
following commands just show me various errors.


any help here that can get me running without having to look at data recovery options?

---

