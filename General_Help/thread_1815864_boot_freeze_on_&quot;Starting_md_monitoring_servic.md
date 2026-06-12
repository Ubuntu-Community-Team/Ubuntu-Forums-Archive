---
title: "boot freeze on &quot;Starting md monitoring service mdadm --monitor        [OK]&quot;"
date: 2011-08-01
forum: General Help
---

### Post by cherva on 2011-08-01
I have ubuntu server 10.04 LTS with two 1TB disks on the two disks I have 2 partitions: one 2gb swap partition and the rest of the space is for /. Two by two are grouped together in raid 1 array ( the two 2gb partitions in md0 and the other two partitions in md1 ) md0 and md1 are both healthy as I can see in /proc/mdstat in recovery mode, but when I try normal boot it freezes on "Starting md monitoring service mdadm --monitor        [OK]". The first boot after the install worked with no problems until the first restart....
Any ideas how to fix this ?

---

