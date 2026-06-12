---
title: "System backup (Criticize, please!)"
date: 2010-11-09
forum: General Help
---

### Post by Vetal_ca on 2010-11-09
Ubuntu 10.04

I need to do full system copy, the Acronis way.

I have 2 HDDs, ext4:

1) System ('/'). Mounted as 'media/System' in LiveCD
2) Big ([SIZE=2]/mnt/Big[/SIZE]). Mounted as 'media/Big' in LiveCD

I'm going to do following steps:

a) Run full copy from LiveCD:
```
sudo rsync -a --delete --progress --exclude-from  '/media/Big/Backups/Linux_exclude.txt' /media/System/  /media/Big/Backups/Linux/
```b) Regilar Linux session, move everything to one binary file, preserving all content, structure and permissions:
```
[SIZE=2]sudo tar -pcvf /mnt/Big/Backups/Linux_Nov_10,_2010.tar /mnt/Big/Backups/Linux[/SIZE]
```c) Winrar it in windows, considering it's compression ratio and recovery capabilities.

Will I have 1:1 system copy? Besides partition's structure and boot sect, of course. But with GRUB config

Thanks

---

