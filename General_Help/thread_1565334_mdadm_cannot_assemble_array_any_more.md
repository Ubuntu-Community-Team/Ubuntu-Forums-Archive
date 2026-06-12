---
title: "mdadm: cannot assemble array any more"
date: 2010-08-31
forum: General Help
---

### Post by mzh on 2010-08-31
Hello,

I'm a quite unexperienced user so please forgive me if I make some rookie mistakes here...

My problem:

I have a raid6 volume, built up from nine identical drives. I've noticed  some days ago that the volume somehow became read-only: the volume is also used as a SMB share, I was trying to copy some data on it over LAN  from windows boxes. Since I was in a hurry I simply (properly) rebooted the box but afterwards the volume won't get assembled again.


 

As I can see it, all the disks are physically present:
 

root@tank:~# fdisk -l |grep GB
 ...
 /dev/sda lemez: 1000.2 GB, 1000204886016 bájt
 /dev/sdb lemez: 1000.2 GB, 1000204886016 bájt
 /dev/sdc lemez: 1000.2 GB, 1000204886016 bájt
 /dev/sdd lemez: 1000.2 GB, 1000204886016 bájt
 /dev/sde lemez: 500.1 GB, 500107862016 bájt
 /dev/sdf lemez: 1000.2 GB, 1000204886016 bájt
 /dev/sdg lemez: 1000.2 GB, 1000204886016 bájt
 /dev/sdh lemez: 1000.2 GB, 1000204886016 bájt
 /dev/sdi lemez: 1000.2 GB, 1000204886016 bájt
 /dev/sdj lemez: 1000.2 GB, 1000204886016 bájt
 



But somehow four of them got out of the volume definition:
 

root@tank:~# cat /proc/mdstat
  Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
 md0 : inactive sdb[5](S) sdc[9](S) sda[6](S) sdf[0](S) sdd[7](S)
       4883812480 blocks
 

 unused devices: <none>
 



Strangely, when scanning for the array, the result slightly differ:
 

root@tank:~# mdadm --assemble --scan
  mdadm: no devices found for /dev/md0
 mdadm: /dev/md/0 assembled from 5 drives and 1 spare - not enough to start the array.
 



Of course i've tried to add the devices again:
 

 root@tank:~# mdadm --add /dev/md0 /dev/sdf /dev/sdg /dev/sdh /dev/sdi /dev/sdj
  mdadm: cannot get array info for /dev/md0
 

This message just confused me more and since I have only limited experience with mdadm/raid stuff I  don't know how to proceed here, so any suggestion/help is most  appreciated.

 

Regards,
mzh

---

