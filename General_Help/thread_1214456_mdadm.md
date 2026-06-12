---
title: "mdadm"
date: 2009-07-15
forum: General Help
---

### Post by erlanning on 2009-07-15
Hi There.
I rushed through my initial set up of mdadm and now I have a few errors.
mdadm -Es reports to arrays both on the same device.
ARRAY /dev/md0 level=raid1 num-devices=5 UUID=b81626d8:886fc990:eb2cb3a3:afdeff67
ARRAY /dev/md0 level=raid5 num-devices=5 UUID=a8b8433f:0b0ebb09:eb2cb3a3:afdeff67

cat /proc/mdstat reports
md_d0 : inactive sdb[0](S)
      976762496 blocks

I cannot --fail or --remove any devices attached to these arrays as mdadm reports that /dev/md0 is not valid.

Also, /etc/mdadm/mdadm.conf reports no information at all.
I have tried to remove and re-install mdadm several time with the same results.

How can I wipe the drives completely so there is not RAID information on them... As well, how do I tell mdadm that it wrong or that it should drop any record of the arrays?

Thanks,
Eric

---

### Post by discodan on 2009-07-17
Here's my two cents worth...

mdadm --stop /dev/md_d0

then:

fdisk -l | more

then for each /dev/sdXn that is setup for Linux raid autodetect:

mdadm --zero-superblock /dev/sdXn

examples:  
mdadm --zero-superblock /dev/sda1
mdadm --zero-superblock /dev/sdb1
mdadm --zero-superblock /dev/sdc1
etc...

this should wipe out any mdadm data that is on the partitions

finally:

bash /usr/share/mdadm/mkconf > /etc/mdadm/mdadm.conf

this will reconstruct your mdadm.conf so that both the previously created /dev/md0 arrays are no longer recognized by mdadm

usually when I do this, I reboot then do:

more /proc/mdstat

to see if it worked.  If it did, no arryas should be listed.

Then recreate your array as you did before.  When you're finished be sure to run:

bash /usr/share/mdadm/mkconf > /etc/mdadm/mdadm.conf

This will ensure that your newly created array is added to the mdadm.conf file.

hope this helps,

if not let me know...


-disco-

---

