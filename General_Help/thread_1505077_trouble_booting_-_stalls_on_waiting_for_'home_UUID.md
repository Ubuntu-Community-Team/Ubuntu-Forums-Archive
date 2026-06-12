---
title: "trouble booting - stalls on waiting for '/home UUID ****'"
date: 2010-06-08
forum: General Help
---

### Post by ghostcoil on 2010-06-08
i restarted my computer (using the button on the tower) while it was frozen while recording with audacity... upon reboot, i received the message:

```
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for a recovery shell)
/home: waiting for UUID=021d0710-c169-4ba7-a640-ee2835f85724
```running fsck in the recovery shell yields warns that sda2 is mounted and that this may lead to SEVERE filesystem damage... so umount sda2 and fsck:

```
e2fsck 1.41.9 (22-Aug-09)
/dev/sda2: clean, 295022/610800 files, 1325916/2441880 blocks
fsck.ext4: Unable to resolve 'UUID=021d0710-c169-4ba7-a640-ee2835f85724'
```i read a few threads that examined blkid and /etc/fstab so i did the same:

blkid
```
/dev/sda1: UUID="5fdf8cd8-bdc1-4fcc-b319-edffefb68262" TYPE="swap"
/dev/sda2: UUID="762ef6cc-1dab-49e4-b9a9-bb3ea8b96ae9" TYPE="ext4"

```cat /etc/fsatbv (info about cdroms/floppies omitted)
```
# / was on /dev/sda2 during installation
UUID=762ef6cc-1dab-49e4-b9a9-bb3ea8b96ae9  /  ext4  errors=remount-ro  0  1
 /home was on /dev/sda3 during installation
UUID=021d0710-c169-4ba7-a640-ee2835f85724  /home  ext4  defaults  0  2
 swap was on /dev/sda1 during installation
UUID=5fdf8cd8-bdc1-4fcc-b319-edffefb68262  none  swap  sw  0  0

```the UUID's match, and the hurdle seems to be on sda3. i tried mounting it with mount:
```
mount: can't find /dev/sda3 in /etc/fstab or /etc/mtab
```any help would be appreciated!

---

### Post by ghostcoil on 2010-06-08
never mind! i ran "fsck /dev/sda3" and after many, many presses of the y button booting is now problem-free and the data seems okay.

looooooove ubuntu!

---

