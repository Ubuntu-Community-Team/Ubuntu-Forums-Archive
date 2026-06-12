---
title: "HDD both NTFS and FAT32"
date: 2006-03-17
forum: General Help
---

### Post by Xecuter on 2006-03-17
I've quickformated a hdd in Windows to NTFS. So Windows says it's NTFS.
But when I boot Ubuntu, it's says the hdd is formated in FAT32.

The problem is when I try to mount it. I can't mount it as NTFS, because Ubuntu thinks it's FAT32, but I can't mount it as FAT32 either, cause I guess it's not looking like a FAT32 filesystem, and then Ubuntu gets comfused. I can't reformat the hdd either cause I have a lot on it.

Need some help!

(Moved this thread here)

---

### Post by mvaniersel on 2006-03-17
Perhaps the information in your /etc/fstab is wrong or outdated since your last format. What does it say there, ntfs or fat?

---

### Post by steve.horsley on 2006-03-17
[QUOTE=mvaniersel]Perhaps the information in your /etc/fstab is wrong or outdated since your last format. What does it say there, ntfs or fat?[/QUOTE]
You can find out with the console command: **sudo fdisk -l**

---

### Post by Xecuter on 2006-03-17
/etc/fstab says "vfat". But so does Disk Manager also.

I'll try running fdisk.

---

### Post by killua_kd on 2006-03-17
then either change the fstab so it say ntfs and just "sudo mount /dev/sda1(use the device to your hdd)" or delete the line and mount it like this "sudo mount -t ntfs /dev/sda1(use the device to your hdd)  /meida/hdd(the mount point)"

---

