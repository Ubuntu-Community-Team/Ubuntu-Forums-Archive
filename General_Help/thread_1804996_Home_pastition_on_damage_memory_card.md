---
title: "Home pastition on damage memory card"
date: 2011-07-15
forum: General Help
---

### Post by pjalegria on 2011-07-15
Hi

I have my home partition installed on a SD memory card, this memory card was damaged beyond recovery, already bought a new card but i dont want to install the OS all over again, how can I fix this?

THX

---

### Post by dabl on 2011-07-15
If you can boot a Live CD, then you have a couple of steps:

1. Use GParted (or fdisk in a terminal) to make a partition table on the new SDHC card, and make a new partition consisting of the entire available space.

2. Use GParted (or mke2fs in a terminal) to make an ext2 filesystem on the partition on the SDHC card.  (You could make it ext3 or ext4, but the journalling is going to beat on the flash media and reduce its useful life. You could also make ext4 and use the "commit=n" mount option, and set the journal writing to a longer interval than the default 5 seconds, like maybe 120 seconds).

3. Open a terminal and run ```
sudo blkid
``` to learn the UUID of the new filesystem on the SDHC card.

4. Still with the Live CD session, mount the root filesystem and edit the file /etc/fstab, to change the UUID for the /home filesystem to the one that you discovered in Step 3 above.  (I'm assuming you are using the default "mount by-uuid" numbering system in /etc/fstab).

Now you should be able to shutdown the Live CD and reboot your system and have /home automatically mounted.

---

### Post by pjalegria on 2011-07-15
Im going to try... thanks

---

### Post by TunaCanTommy on 2011-07-18
Assumiing you have /home installed on a funtioning SD card - all the files are intact.  And you want to put a larger capacity card in it's place.  At what point in the above procedure, and what command would you use, to move all the files to the new, larger SD card ?

Edit: Did more looking and I believe I found it . . . 

               sudo rsync -axS --exclude='/*/.gvfs' /home/. /media/home/.

---

