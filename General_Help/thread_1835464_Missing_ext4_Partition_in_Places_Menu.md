---
title: "Missing ext4 Partition in Places Menu"
date: 2011-08-29
forum: General Help
---

### Post by ShodanjoDM on 2011-08-29
Hi all

I'm using Ubuntu 11.04 in two partitions (/dev/sda1 for standard Ubuntu/Gnome 2 install & /dev/sda4 for Ubuntu + Gnome 3). I could no longer see the /dev/sda4 - labelled as Ubuntu-2 - listed in Places menu since yesterday. And it's also missing from "Computer" in Nautilus.

I still can mount it manually using "sudo mount" command and have already checked the partition, but I want to know how to bring it back to Places menu for convenience sake.

here's my fdisk -l output:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00009fb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2439    19582976   83  Linux
/dev/sda2            4877       60315   445312000   83  Linux
/dev/sda3           60315       60802     3907584   82  Linux swap / Solaris
/dev/sda4            2439        4877    19582976   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003e32e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           38653       38914     2098690   82  Linux swap / Solaris
/dev/sdb2               1        2611    20972826   83  Linux
/dev/sdb4            2612       38652   289499332+  83  Linux

Partition table entries are not in disk order

```

Many thanks in advance :)

---

### Post by seawolf167 on 2011-08-29
When you manually mount it does it also add the "Places" menu entry? If so, you probably don't have (and need to add) an entry for the device in /etc/fstab.

If so, please also post the output of 

```
sudo blkid
```

so we can get you the correct entry to add

---

### Post by ShodanjoDM on 2011-08-29
I have to make a new folder in /media for it to appear in Places menu otherwise it won't show up.

For a test, I made a new "Ubuntu2" folder in /media (for not messing with the partition label of "Ubuntu-2" which appeared in Places Menu before - just in case), run "mount /dev/sda4 /media/Ubuntu2" and it appears there.

Here's my blkid:

```
/dev/sda1: LABEL="Ubuntu-1" UUID="7154b84c-603b-4c2c-8fd6-ff8064ec323d" TYPE="ext4" 
/dev/sda2: LABEL="Home" UUID="68003286-fab4-47b0-ac43-894d76827d04" TYPE="ext4" 
/dev/sda3: UUID="4350a5f7-a56c-4af4-bff1-3f1f993e22c9" TYPE="swap" 
/dev/sda4: LABEL="Ubuntu-2" UUID="90fb711a-d335-4394-ac45-a230fe26877c" TYPE="ext4" 
/dev/sdb1: UUID="13ac66e0-7308-4f6d-8fdc-93fb4c2b0522" TYPE="swap" 
/dev/sdb2: LABEL="Arch64" UUID="dbffbb35-ba85-4298-b98f-e148f472b1d2" TYPE="ext4" 
/dev/sdb4: LABEL="Home" UUID="acf222db-5aa1-46b7-9ca6-84c72d558d5b" TYPE="ext4"
```

Don't know if this is related, but the problem appear yesterday after I installed e17, I have removed it but the problem persists.

---

### Post by seawolf167 on 2011-08-29
Try adding your /etc/fstab line then and it should work.

Open /etc/fstab for editing

```
gksu gedit /etc/fstab
```add the following line at the bottom, save, and exit

```
# Ubuntu-2 entry
UUID=90fb711a-d335-4394-ac45-a230fe26877c /media/Ubuntu2 ext4 defaults 0 0
```note that "Ubuntu2" is case-sensitive, so ensure that this is the exact same name as the folder you created previously.

---

### Post by ShodanjoDM on 2011-08-29
Thank you, but I forgot to mention that I'm already familiar with fstab editing. It's not that I want the partition to auto-mount everytime I logged in, I'm just curious about how to bring the "Ubuntu-2" entry back in Places Menu where I can just click to mount and unmount the partition without having to create a mount point in /media first...

But thanks again, much appreciated :)

---

### Post by ShodanjoDM on 2011-08-29
Found an "unelegant" solution:

Made a backup of /dev/sda4, re-format it to create a new UUID & re-label it as a new "Ubuntu-2" partition using gparted. And the partition's label appears again on the Places menu. 

Since that is another Ubuntu installation's root partition, I have to edit Ubuntu-2's fstab to change / UUID with the new one.

Oh well, atleast it works now :p and I'm marking this thread as solved.

---

