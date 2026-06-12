---
title: "Question about permanently mounting a drive"
date: 2011-01-10
forum: General Help
---

### Post by riprowan on 2011-01-10
I followed the directions located [here]("https://help.ubuntu.com/community/MountingWindowsPartitions") to permanently mount my drives in 10.10 and had several problems.

First off, I installed NTFS-config as suggested.  It will not run.  After entering my Administrator password, the program vanishes.

QUESTION 1 - why doesn't this work?

Secondly, I used the instructions to mount the drives by editing my fstab.  My drives mount, however, there remains an additional, unmounted "copy" of the drives in my "Places" list.

QUESTION 2 - how do I fix this?

TIA,
Rip

---

### Post by Bucky Ball on 2011-01-10
Check you have NTFS-3g installed. NTFS-config is the GUI for using it manually but you shouldn't need to. NTFS-3g should be installed by default but I suspect in your case it wasn't.

Open file manager and in the bottom pane of the left hand column you should have the same as in 'Places'. Delete what you don't want. Drag the folders you want in 'Places' from the filemanager right pane to the bottom left pane instead (this will create shortcuts, naturally, not move the folder there as this can't be done in that pane).

---

### Post by Morbius1 on 2011-01-10
> Secondly, I used the instructions to mount the drives by editing my  fstab.  My drives mount, however, there remains an additional, unmounted  "copy" of the drives in my "Places" list.
Please post the output of these two commands:
```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```

---

### Post by riprowan on 2011-01-10
> **Morbius1 said:**
> Please post the output of these two commands:
```
sudo blkid -c /dev/null
```

```
/dev/sda1: LABEL="System Reserved" UUID="E27437B774378D73" TYPE="ntfs" 
/dev/sda2: UUID="B2EC395DEC391D53" TYPE="ntfs" 
/dev/sda5: UUID="6ebc66bf-530f-462f-84c1-eb35fd72a12a" TYPE="ext4" 
/dev/sda6: UUID="c8019836-295f-4959-a834-a0d959fd9678" TYPE="swap" 
/dev/sdb1: LABEL="Data" UUID="5C104A3A104A1B80" TYPE="ntfs" 
/dev/sdc1: LABEL="Backup" UUID="AC18214218210CC0" TYPE="ntfs"
```

> **Morbius1 said:**
> ```
cat /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=6ebc66bf-530f-462f-84c1-eb35fd72a12a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c8019836-295f-4959-a834-a0d959fd9678 none            swap    sw              0       0
UUID=5C104A3A104A1B80 /media/data ntfs-3g defaults,user,locale=en_US.utf8 0 0
UUID=AC18214218210CC0 /media/backup ntfs-3g defaults,user,locale=en_US.utf8 0 0
```

---

### Post by Morbius1 on 2011-01-10
Although one can debate the usefulness of the "user" option in your fstab entries all that should work.

There is a very old bug that just won't go away that describes the duplication in nautilus: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130)

You can test it out by unmounting one of those partitions:
```
 sudo umount /media/data
```Then changing the line in fstab to :
>  [COLOR=Blue]/dev/disk/by-uuid/[/COLOR]5C104A3A104A1B80 /media/data ntfs-3g defaults,user,locale=en_US.utf8 0 0Save fstab and run the following command:
```
sudo mount -a
```If that command runs without errors restart Nautilus and see if the problem went away.

---

