---
title: "Restoring FSTAB"
date: 2012-07-03
forum: General Help
---

### Post by SuperFreak on 2012-07-03
I am not getting replies on a previous post and the nature of the problem has morphed a bit away from the original issue.
My Fstab file has changed for some reason and no longer lists / or Home partitions so the computer will not boot properly (I can just get into the guest account not my own). I have an old copy of FSTAB (see 2nd screenshot) and wonder if I should replace the present FSTAB(1st screenshot) with that. I am not sure if it is optimized for my SSD where / is located but it might be a start. Advice would be welcome. I assume I would edit FSTAB from a live copy of Ubuntu?
The problems started when I was backing up files to DATA COPY which is not supposed to be in Fstab

---

### Post by dino99 on 2012-07-03
you need to be sure about your actual uuids:

sudo blkid

then edit your fstab to update it if it need to:

gksu gedit /etc/fstab

mine, for example:

proc /proc proc defaults 0 0
UUID=00c5de83-479c-4ab0-9b54-9af0a727175e / ext4 defaults,errors=remount-ro,relatime 0 1
UUID=0a9ca7f0-6eeb-4b21-b70f-670fa600de16 none swap sw 0 0
UUID=5d8d1ee1-f5af-40a1-a45d-dbc570808523 /home ext3 defaults 0 2
/dev/disk/by-id/ata-TSSTcorp_CDDVDW_SH-S203D /mnt/ata-TSSTcorp_CDDVDW_SH-S203D auto nosuid,nodev,nofail,noauto,x-gvfs-show 0 0

---

### Post by SuperFreak on 2012-07-03
Thanks for reminding me about blkid
At first it didn't boot correctly but one partition (EFI) had the wrong UUID and after correcting it it seems to work fine.

---

