---
title: "An superblock tale of woe"
date: 2012-08-01
forum: General Help
---

### Post by Alabamian on 2012-08-01
Goodly men and womenfolk of Ubuntu-land.  My tale starts with many electrical blackouts, followed by an exploding graphics card, with the end result a system that, when booting, gives continuous Input Output errors and boot-eth not.

Herein follows a saga of tragedy not told since days of Romeo and Juliet.  sda1, the GhostBoot partition, appeareth fine, and verily, the NTFS partition, yea, even Windows 7, boot-eth fine and workest in all forms.  Tis the Linux partition that booth-eth not, up to the point of not being address-able in any fashion.  I should merely hope to mount the volume and save the data, and start over with the option nuclear pavement.  But the data yet hast reached salvation, and this end doth I seek.

1)  What sayeth fdisk?

```
knoppix@Microknoppix:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x9201fe6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           2       16033+   1  FAT12
/dev/sda2               3       50994   409593240    7  HPFS/NTFS
/dev/sda3           50995      121601   567150727+  8e  Linux LVM

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x9201fe50

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          15      120456   83  Linux
/dev/sdb2              16      121602   976641024   8e  Linux LVM
knoppix@Microknoppix:~$

```

2)  What more sayeth fdisk?

```
knoppix@Microknoppix:~$ sudo fdisk -l /dev/sda3

Disk /dev/sda3: 580.8 GB, 580762344960 bytes
255 heads, 63 sectors/track, 70607 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x00000000

Disk /dev/sda3 doesn't contain a valid partition table

knoppix@Microknoppix:~$ sudo mke2fs -n /dev/sda3
warning: 545 blocks unused.

Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
35516016 inodes, 141787136 blocks
7089384 blocks (5.00%) reserved for the super user First data block=0 Maximum filesystem blocks=0
4327 block groups
32768 blocks per group, 32768 fragments per group
8208 inodes per group
Superblock backups stored on blocks:
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
	102400000

```

3)  Mounteth not, read-only

```
knoppix@Microknoppix:~$
knoppix@Microknoppix:/media$ sudo mount -o,ro /dev/sda3
mount: unknown filesystem type 'LVM2_member'
knoppix@Microknoppix:/media$


```
4)  O, fsck, what sayest thou?
```
knoppix@Microknoppix:~$ sudo fsck /dev/sda3
fsck: fsck.LVM2_member: not found
fsck: Error 2 while executing fsck.LVM2_member for /dev/sda3 knoppix@Microknoppix:~$


```
5)  And you, e2fsck, what canst thou add to this tale of woe?
```
knoppix@Microknoppix:~$ e2fsck /dev/sda3
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda3

The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

knoppix@Microknoppix:~$
```


6)  mke2fs and e2fsck chant in harmony this Siren saga
```
knoppix@Microknoppix:~$ sudo mke2fs -n /dev/sda3
warning: 545 blocks unused.

Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
35516016 inodes, 141787136 blocks
7089384 blocks (5.00%) reserved for the super user First data block=0 Maximum filesystem blocks=0
4327 block groups
32768 blocks per group, 32768 fragments per group
8208 inodes per group
Superblock backups stored on blocks:
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
	102400000


knoppix@Microknoppix:~$ sudo e2fsck -y -b 32768 /dev/sda3
e2fsck: Bad magic number in super-block while trying to open /dev/sda3

The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

knoppix@Microknoppix:~$ sudo e2fsck -y -b 98304 /dev/sda3
e2fsck: Bad magic number in super-block while trying to open /dev/sda3

The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


knoppix@Microknoppix:~$ sudo e2fsck -y -b 163840 /dev/sda3
e2fsck: Bad magic number in super-block while trying to open /dev/sda3

The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

knoppix@Microknoppix:~$ sudo e2fsck -y -b 229376 /dev/sda3
e2fsck: Bad magic number in super-block while trying to open /dev/sda3

The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

knoppix@Microknoppix:~$

etcetera, etcetera until ...

knoppix@Microknoppix:~$ sudo e2fsck -y -b 102400000 /dev/sda3
e2fsck: Invalid argument while trying to open /dev/sda3

The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

knoppix@Microknoppix:~$
```

---

### Post by steeldriver on 2012-08-01
if (as indicated by fdisk) your actual filesystem (ext2/3/4 or whatever) is on top of an lvm volume, then you will need to mount *that* - I don't think you will be able to mount /dev/sda3 directly

what do you get if you do

```
sudo pvdisplay
sudo vgdisplay
sudo lvdisplay
```

---

### Post by Alabamian on 2012-08-01
```
knoppix@Microknoppix:~$ sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/sda3
  VG Name               system
  PV Size               540.88 GiB / not usable 2.13 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              138464
  Free PE               0
  Allocated PE          138464
  PV UUID               82mlan-AKXb-Ez6M-LRG5-WBLj-RLYf-KtSvhG

  --- Physical volume ---
  PV Name               /dev/sdb2
  VG Name               system
  PV Size               931.40 GiB / not usable 3.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              238437
  Free PE               0
  Allocated PE          238437
  PV UUID               jsn4Jk-Uv4r-kRcC-Yg0f-6BUl-0no4-XiTpnW

knoppix@Microknoppix:~$ sudo vgdisplay
  --- Volume group ---
  VG Name               system
  System ID
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               0
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               1.44 TiB
  PE Size               4.00 MiB
  Total PE              376901
  Alloc PE / Size       376901 / 1.44 TiB
  Free  PE / Size       0 / 0
  VG UUID               1W2pVe-uIE1-ZfWk-X7lq-kTwc-bl65-GWgVAh

knoppix@Microknoppix:~$ sudo lvdisplay
  --- Logical volume ---
  LV Name                /dev/system/root
  VG Name                system
  LV UUID                kp4SIN-jUk5-kdwH-NY8n-Eeif-1Sc6-pC1Kz0
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                1.37 TiB
  Current LE             360261
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto

  --- Logical volume ---
  LV Name                /dev/system/swap
  VG Name                system
  LV UUID                zppSye-2m23-f9dh-dKcb-7Qdw-zDKX-Z0HuTN
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                65.00 GiB
  Current LE             16640
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto

knoppix@Microknoppix:~$
```

And thank you, Steeldriver, in advance.

---

### Post by steeldriver on 2012-08-01
OK, so what happens if you run

```
sudo lvchange -ay /dev/system/root
```Does the status show as 'available' if you run lvdisplay again? 

```
sudo lvdisplay /dev/system/root
```Also, let's have a look at your /etc/fstab to see how the volume was originally mounted

```
cat /etc/fstab
```

---

### Post by Alabamian on 2012-08-01
```
knoppix@Microknoppix:~$ sudo lvchange -ay /dev/system/root
  The link /dev/system/root should had been created by udev but it was not found. Falling back to direct link creation.
knoppix@Microknoppix:~$ sudo lvdisplay /dev/system/root
  --- Logical volume ---
  LV Name                /dev/system/root
  VG Name                system
  LV UUID                kp4SIN-jUk5-kdwH-NY8n-Eeif-1Sc6-pC1Kz0
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                1.37 TiB
  Current LE             360261
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0

knoppix@Microknoppix:~$ cd /dev/system/root
bash: cd: /dev/system/root: Not a directory 

knoppix@Microknoppix:~$ cat /etc/fstab # DEFAULT BASE FSTAB, UNCONFIGURED
proc       /proc         proc       noauto             0 0
sysfs      /sys          sysfs      noauto             0 0
# Added by KNOPPIX
/dev/sr0 /media/sr0 iso9660 noauto,users,exec 0 0 # Added by KNOPPIX
/dev/sdb2 /media/sdb2 LVM2_member noauto,users,exec 0 0 # Added by KNOPPIX
/dev/sdb1 /media/sdb1 ext4 noauto,users,exec 0 0 # Added by KNOPPIX
/dev/sda2 /media/sda2 ntfs
noauto,users,exec,umask=000,uid=knoppix,gid=knoppix 0 0 # Added by KNOPPIX
/dev/sda1 /media/sda1 vfat
noauto,users,exec,umask=000,shortname=winnt,uid=knoppix,gid=knoppix 0
0
# Added by KNOPPIX
/dev/sda3 /media/sda3 LVM2_member noauto,users,exec 0 0 knoppix@Microknoppix:~$
```

---

### Post by nothingspecial on 2012-08-01
Wouldst that thine fine cousin hadst enclosed yon verse in tags of code that every eye could behold it readily.

---

### Post by steeldriver on 2012-08-01
Oops sorry - had a bit of a brainfart there, obviously you are booting from a live recovery cd and the fstab I was interested in will be on the system that you can't boot

Nevertheless your original root lv should now be available via /dev/mapper and you can check its filesystem type using 

```
sudo parted /dev/mapper/system-root print
```or

```
sudo file -sL /dev/mapper/system-root
```If that looks OK you should be able to mount the volume using the same /dev/mapper/*vgname*-*lvname* label (you may need to unmount the raw /dev/sda3 device first, I don't know for sure)

---

### Post by Alabamian on 2012-08-01
Steeldriver, another interesting development is seen in Knoppix' XWindowing environment.  I now see a volume "dm-0" on the Graphical Desktop.  When I try and click on it I get a message that says ...

Authentication is required to mount the device

An application is attempting to perform an action that requires privileges.  Authentication is required to perform this action.
  Password:  _________________

v Details
  Action:  org.freedesktop.udisks.filesystem-mount-system-internal
  Vendor:  the udisks Project

with Cancel and Authenticate buttons at the bottom of the screen.

Then, after about 10 seconds not clicking anything, this daughter pop-up says ...

Did not receive a reply.  Possible causes include:  the remote application did not send a reply (wow, now a silly Knoppix CD is calling ME a remote application!), the message bus security policy blocked the reply (somebody call security), the reply time out expired (now that's more like it), or the network connection was broken.  There's an Okay button to close this daughter pop-up.

---

### Post by Alabamian on 2012-08-01
Duh, one detail I failed to mention.  I have asked the end-user for his root password, which he claims to have given me.  I'm not certain this was just his sudoer user account password, but I honestly don't have any other information to go off of.  I have a sudoer admin account on the box, too, but my password doesn't work, either.

---

### Post by steeldriver on 2012-08-01
Yes dm-0 would likely be the actual block device corresponding to the lvm volume, e.g. on my system I get

```
~$ ls -l /dev/mapper/vg0-lv0
lrwxrwxrwx 1 root root 7 2012-08-01 13:07 /dev/mapper/vg0-lv0 -> ../dm-3
~$

```

Unless the volume is encrypted the only elevated permission you should need in order to mount / read it is sudo for the knoppix live system.

---

### Post by Alabamian on 2012-08-01
First, nobodyspecial, I'm sorry but I haven't installed JavaScript on this copy of Knoppix, so I can't read the blog specs.  Not trying to avoid the rules, but ...

Steeldriver, THANK YOU!

I did this ...

knoppix@Microknoppix:/dev/mapper$ ls -all
total 0
drwxr-xr-x  2 root root      80 Aug  1 11:36 .
drwxrwxrwt 24 root root   18700 Aug  1 11:36 ..
crw-------  1 root root 10, 236 Aug  1 08:39 control
lrwxrwxrwx  1 root root       7 Aug  1 12:47 system-root -> ../dm-0
knoppix@Microknoppix:/dev/mapper$ ls -l system-root
lrwxrwxrwx 1 root root 7 Aug  1 12:47 system-root -> ../dm-0
knoppix@Microknoppix:/dev/mapper$ sudo mount system-root /mnt
knoppix@Microknoppix:/dev/mapper$ cd ..
knoppix@Microknoppix:/dev$ cd ..
knoppix@Microknoppix:/$ cd mnt
knoppix@Microknoppix:/mnt$ ls
C:\nppdf32Log\debuglog.txt  home             media  run      sys
bin                         lib              mnt    sbin     tmp
boot                        lib64            opt    selinux  usr
dev                         lost+found       proc   srv      var
etc                         maple15.desktop  root   success  windows

... and I was in like Flynn!  After sudo chown-ing the user's home directory (got errors copying first, so I did that and then chmod-ed o+r a subdirectory that still gave me errors after that)  I'm copying off the various local gigabytes of stranded data to a big-drived server right now.  Hallelujah, baby!  Now the only errors I'm getting have to do with duplicate files (destination server is smb, so capital letter differences, no biggie) and symlink errors (yeah, right, like those are gonna work).  But his gigabytes of critical data are on their way to backed up server heaven.

Yea, verily, Amen.  Hallowed be thou, Steeldriver, amongst the sons of Adam!

---

### Post by steeldriver on 2012-08-01
Glad it worked out for you :)

---

