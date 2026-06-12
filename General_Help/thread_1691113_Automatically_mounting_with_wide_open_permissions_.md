---
title: "Automatically mounting with wide open permissions a FAT formatted USB flash drive"
date: 2011-02-19
forum: General Help
---

### Post by Geojay on 2011-02-19
I have a netbook running Ubuntu Netbook Edition and I would like a USB flash drive to be automatically mounted whenever I plug it in. The drive is FAT formatted. It mounts when I plug it in but all files are only writable by my user, other users only have read access. I understand that I need to add a corresponding entry to the /etc/fstab file. I've added the following so far:
/dev/sdb1 /mnt/USB_DRIVE vfat

Firstly, is that appropriate so far? I've created /mnt/USB_DRIVE as root. 

Next, I'm not sure what options I should be finishing the line with, especially to get all users to be able to write to the drive. 

All suggestions gratefully received!

Thanks

---

