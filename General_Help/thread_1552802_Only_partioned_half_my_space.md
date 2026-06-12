---
title: "Only partioned half my space?"
date: 2010-08-14
forum: General Help
---

### Post by domzz on 2010-08-14
I have 2x 1TB drives:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00060cef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406   fd  Linux RAID autodetect
/dev/sda2            1276      121536   965995107   fd  Linux RAID autodetect
/dev/sda3          121536      121601      523488   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00072acd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1275    10241406   fd  Linux RAID autodetect
/dev/sdb2            1276      121536   965995107   fd  Linux RAID autodetect
/dev/sdb3          121536      121601      523488   82  Linux swap / Solaris

Disk /dev/md1: 10.5 GB, 10487070720 bytes
2 heads, 4 sectors/track, 2560320 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md2: 989.2 GB, 989178888192 bytes
2 heads, 4 sectors/track, 241498752 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

```

But when I check 
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/md1              9.7G  2.5G  6.8G  27% /
none                  4.0G  212K  4.0G   1% /dev
none                  4.0G     0  4.0G   0% /dev/shm
none                  4.0G  100K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
none                  4.0G     0  4.0G   0% /lib/init/rw
none                  9.7G  2.5G  6.8G  27% /var/lib/ureadahead/debugfs
/dev/md2              914G  200G  669G  23% /home
```

I only have 914G space...

---

### Post by Quackers on 2010-08-14
Is it set up in raid 1 ?

---

### Post by domzz on 2010-08-14
Im a total noob when it comes to raid: but
```
# cat /proc/mdstat
Personalities : [raid1] [raid0] [raid6] [raid5] [raid4] [linear] [multipath] [raid10] 
md2 : active raid1 sdb2[1] sda2[0]
      965995008 blocks [2/2] [UU]
      
md1 : active raid1 sdb1[1] sda1[0]
      10241280 blocks [2/2] [UU]

```

---

### Post by Quackers on 2010-08-14
I'm no expert either, so you're in good company :-)
However, it looks to me like you are in raid 1. Otherwise known as a mirror or mirrored. That means you have 2 drives and they are each a copy of the other. If one drive breaks you can replace it and your system should be rebuilt from the other disc (maybe even automatically). Basically your 2 x 1TB discs have become one 1TB disc with a copy on the other disc. Your total disc storage is therefore only 1TB.
If the raid array was in raid 0 you would have your total storage of 2 x 1TB back and read/write access speeds would be quicker. BUT you would have no redundancy (backup copy on the second disc). So if one disc fails you lose all data on both discs.
If you want to change from raid 1 to raid 0 or delete the raid array completely you will almost certainly lose everything on both discs.

---

### Post by domzz on 2010-08-14
> **Quackers said:**
> I'm no expert either, so you're in good company :-)
However, it looks to me like you are in raid 1. Otherwise known as a mirror or mirrored. That means you have 2 drives and they are each a copy of the other. If one drive breaks you can replace it and your system should be rebuilt from the other disc (maybe even automatically). Basically your 2 x 1TB discs have become one 1TB disc with a copy on the other disc. Your total disc storage is therefore only 1TB.
If the raid array was in raid 0 you would have your total storage of 2 x 1TB back and read/write access speeds would be quicker. BUT you would have no redundancy (backup copy on the second disc). So if one disc fails you lose all data on both discs.
If you want to change from raid 1 to raid 0 or delete the raid array completely you will almost certainly lose everything on both discs.


Thanks, I don't really know how raid works... but thats a great answer :) 

At the moment, I don't need the second drive but when I do, can I change it to raid 0 with out problems?

---

### Post by linux18 on 2010-08-14
"Disk /dev/md1 doesn't contain a valid partition table"

that kind of explains it, you need to reformat the drive, this time changing the partition table.
backup the data, goto gparted > device > create partition table. then format ext4, then your good to go

edit: remove the other drive, if it is raid1 reformatting won't go so well

---

### Post by Quackers on 2010-08-14
There are other problems in store for you.
If you delete the raid array (probably in bios) your discs will become unreadable and the data that's already on them will be lost.
If you leave the raid array alone you may be able to just create a partition for Ubuntu as Linux18 has said. It is also possible that the raid drivers may cause a problem too.
I would back up everything on the drive at the moment. You should also make sure that your backups can be restored to a raid array - some cannot!

---

### Post by domzz on 2010-08-14
Darn, is there a way without reformatting it? Im using ubuntu1004-server. And I only have 100GB of backup space with my host.

---

### Post by linux18 on 2010-08-14
if your server has a super-fast upload, offload the data to a mediafire account (unlimited uploads and downloads, but a max 200MB file size and every file is public - mabye encrypt, compress, and split? )

---

### Post by Quackers on 2010-08-14
I believe you could run Ubuntu from within Windows (is it a wubi install?) as a virtual system. Maybe look into that.

---

