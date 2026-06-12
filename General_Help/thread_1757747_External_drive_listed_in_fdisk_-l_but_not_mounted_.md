---
title: "External drive listed in fdisk -l but not mounted nor in &quot;Places&quot;"
date: 2011-05-13
forum: General Help
---

### Post by 3602 on 2011-05-13
So the situation is as described... I sincerely do not know what I did. The last time I removed it is through Right Click and "Safely Remove Drive".

In *sudo fdisk -l* I can see it right there, even the tag is good (/dev/sdc and /dev/sdc1).

Thank you very much!

---

### Post by _0R10N on 2011-05-13
> **3602 said:**
> So the situation is as described... I sincerely do not know what I did. The last time I removed it is through Right Click and "Safely Remove Drive".

In *sudo fdisk -l* I can see it right there, even the tag is good (/dev/sdc and /dev/sdc1).

Thank you very much!

Have you tried to mount it manually?

---

### Post by _0R10N on 2011-05-13
> **_0R10N said:**
> Have you tried to mount it manually?

If it's already mounted, it should be listed in the /etc/mtab file.

---

### Post by 3602 on 2011-05-13
Nope, ain't in there. There's *sda sdb sdd* and that's it.
I already tried
```
mount /dev/sdc
```and I get
```
mount /dev/sdc
mount: can't find /dev/sdc in /etc/fstab or /etc/mtab

```Adding sudo changes nothing. Changing *sdc* to *sdc1* and I get the same message.
sudo fdisk -l lists this clear as day:
```
Disk /dev/sdc: 4119 MB, 4119330816 bytes
64 heads, 32 sectors/track, 982 cylinders
Units = cylinders of 2048 * 2048 = 4194304 bytes
Sector size (logical/physical): 2048 bytes / 2048 bytes
I/O size (minimum/optimal): 2048 bytes / 2048 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         982     4021976    b  W95 FAT32

```Four gigs, that is correct.

I can apply *fatsort* on /dev/sdc1 and see its contents. 

Thank you very much.

---

### Post by 3602 on 2011-05-14
Bump.

---

### Post by 3602 on 2011-05-15
Update:
If I follow this here
[https://help.ubuntu.com/community/Mount/USB#Manually%20Mounting]("https://help.ubuntu.com/community/Mount/USB#Manually%20Mounting")
I can get it mounted and read/write it. But when I unmount it, unplug it and plug it back in, it doesn't auto-mount.

Update II: When trying to copy files from the external drive to the Home folder, the entire system will freeze as is the mouse cursor, the keyboard and the screen will become "dead". Trying to switch into the Console (Ctrl - Alt - F1) will not work. The transfer *will *complete, though, as I pulled out the drive when the access lamp went off and forcefully rebooted the computer, the files are there in the Home directory.
I have tried to format this drive on-board but it still would not auto-mount. The manual for this drive specifically points out "Do NOT use a computer to format this device".

Update III: OK, I may have a bit of a breakthrough.
I powered down the drive, shut down the computer, connected the drive to the computer (with the computer still off) then I booted the computer.
In GLX-Dock's "Shortcuts" I can now see my "SONY IC RECORDER". However, when I click on it, it says "Failed to mount SONY IC RECORDER".
In Disk Utility (System - Administration - Disk Utility) I see it and it is partitioned to MBR (Master Boot Record). But gparted crashes on start.

fdisk -l now has a boot star on it:
```
Disk /dev/sdb: 4119 MB, 4119330816 bytes
64 heads, 32 sectors/track, 982 cylinders
Units = cylinders of 2048 * 2048 = 4194304 bytes
Sector size (logical/physical): 2048 bytes / 2048 bytes
I/O size (minimum/optimal): 2048 bytes / 2048 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         982     4021976    b  W95 FAT32

```When I try to fsck it, I get:
```
sudo fsck /dev/sdb1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

---

### Post by 3602 on 2011-05-15
OK I uh... "Solved" this problem by formatting the *Volume* of the drive... Interesting how the ten MSSONY folders are still there but the contents removed.

---

