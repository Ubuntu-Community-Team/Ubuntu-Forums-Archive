---
title: "Trouble getting partitions to mount."
date: 2012-01-31
forum: General Help
---

### Post by theheadlessrabbit on 2012-01-31
I'm having some trouble getting some hard drives and partitions to mount properly.

I've got a dual boot Win7/Ubuntu 11.10 setup. i7, GA-z68xp-ud4 mobo.  

I have 3 physical hard drives, and a lot of partitions:

sda1: ext4, "SSD60"

sdb2: file system: extended (?)
unallocated - 1mb 
sdb8: ext4 "Storage"
sdb7: ntfs "WinStorage"
sdb6: fat32 "FAT32"
sdb5: linux swap
sdb1: /home

sdc1: Win 7
sdc2: ubuntu

When I attempt to boot, I get 3 errors:
"The disk drive for /media/SSD60 is not ready yet  or not present"
"The disk drive for /media is not ready yet or  or not present"
"The disk drive for /media/sdb8 is not ready yet *or not present"

I press "S" to skip through each of these. system loads.

"SSD60" works perfectly. it mounts, I have read write access. no problems other than the annoying error message on start-up.

"Storage", "WinStorage" and "FAT32" will not mount.

If I open up the terminal and type "sudo nautilus" those 3 drives disappear, and all I see under the devices list are 2 drives labeled "media".  If I try to mount them, I get, "Unable to mount media. mount: special device UUID=D913-45B2 does not exist"

If I open up "Gparted", I can mount the drives through that program, but the drives appear under "Computer" rather than "devices" in the window, and they belong to root, not to me.  If I do "sudo nautilus" again and try to change the owner by right clicking, it keeps jumping back to root.  it will not let me change owners.

Here's my "fdisk -l" output, if it helps:
> Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002d7f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   117229567    58613760   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ca786

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1      1753524224  1953523711    99999744   83  Linux
/dev/sdb2            2046  1753524223   876761089    5  Extended
/dev/sdb5      1721524224  1753524223    16000000   82  Linux swap / Solaris
/dev/sdb6      1469865984  1721522175   125828096    b  W95 FAT32
/dev/sdb7      1218207744  1469863935   125828096    7  HPFS/NTFS/exFAT
/dev/sdb8            4096  1218205695   609100800   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b0b37

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   150554623    75276288    7  HPFS/NTFS/exFAT
/dev/sdc2       150554624   234440703    41943040   83  Linux


---

### Post by theheadlessrabbit on 2012-01-31
I should add that BEFORE forcing gparted to mount these partitions, I get this error:

"Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb8 on /media/sdb8"


After forcing Gparted to mount them, clicking on the device icon does nothing.

---

### Post by Dumbestcrayon on 2012-02-01
EDIT: Try running gparted with the following command rather than through the applications menu

```
gksu gparted &
```

Can you mount them and paste the output of the following two commands?

```
cat /etc/fstab
```

```
mount
```

---

### Post by theheadlessrabbit on 2012-02-01
Odd...I've restarted my machine, and now I cannot mount through gparted....

```

[1] 3651
kyle@kyle-Z68XP-UD4:~$ 
(gksu:3651): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:3651): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:3651): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:3651): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
======================
libparted : 2.3
======================
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc         proc  nodev,noexec,nosuid                0  0  
# / was on /dev/sdc2 during installation
UUID=fd4ee5c3-31fa-437f-9d00-3000d0742c10  /             ext4  errors=remount-ro                  0  1  
# /SDD60 was on /dev/sda1 during installation
UUID=9744fdc9-fb68-4969-aeac-ae05311a06c8  /media/SSD60  ext4  defaults                           0  2  
# /dos was on /dev/sdb6 during installation
UUID=D913-45B2                             /media        vfat  owner,umask=007,gid=46,users,user  0  1  
# /home was on /dev/sdb1 during installation
UUID=5a4a6c7f-8bfa-4617-a56b-2a52c50afc99  /home         ext4  defaults                           0  2  
# /storage was on /dev/sdb7 during installation
UUID=a38b17fc-5601-42f5-9484-462c6d59f231  /media        ext4  users,user,owner                   0  2  
# swap was on /dev/sdb5 during installation
UUID=11837edf-77b8-4ff9-b9c4-d953be714d59  none          swap  sw                                 0  0  
/dev/sdb6                                  /media/sdb6   vfat  defaults                           0  0  
/dev/sdb7                                  /media/sdb7   ntfs  defaults                           0  0  
/dev/sdb8                                  /media/sdb8   ext4  defaults                           0  0  
kyle@kyle-Z68XP-UD4:~$ mount
/dev/sdc2 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb1 on /home type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kyle/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kyle)
/dev/sdc1 on /media/5CC45362C4533D88 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1 on /media/SSD60 type ext4 (rw,nosuid,nodev,uhelper=udisks

```

---

### Post by Dumbestcrayon on 2012-02-01
Try this

```
sudo mkdir /media/sdb6-test

sudo mount -t vfat -o defaults,user,exec,uid=1000,gid=100,umask=000 /dev/sdb6 /media/sdb6-test
```

see if that mounts to /media/sdb6-test

---

### Post by theheadlessrabbit on 2012-02-01
```

mount: wrong fs type, bad option, bad superblock on /dev/sdb6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

kyle@kyle-Z68XP-UD4:~$ dmesg | tail
[  387.093866] FAT-fs (sdb6): bogus number of reserved sectors
[  387.093873] FAT-fs (sdb6): Can't find a valid FAT filesystem
[  408.585618] r8169 0000:06:00.0: eth0: link up
[  427.854523] r8169 0000:06:00.0: eth0: link up
[  477.033883] r8169 0000:06:00.0: eth0: link up
[  490.291979] r8169 0000:06:00.0: eth0: link up
[  497.072596] r8169 0000:06:00.0: eth0: link up
[  508.886797] r8169 0000:06:00.0: eth0: link up
[  545.410368] r8169 0000:06:00.0: eth0: link up
[  563.905474] r8169 0000:06:00.0: eth0: link up

```

---

### Post by oldfred on 2012-02-01
These two entries in fstab cannot be correct. You cannot mount to media without creating a mount point and using that mount.

> # /dos was on /dev/sdb6 during installation
UUID=D913-45B2                            [COLOR=Red] /media [/COLOR]       vfat  owner,umask=007,gid=46,users,user  0  1  

# /storage was on /dev/sdb7 during installation
UUID=a38b17fc-5601-42f5-9484-462c6d59f231  [COLOR=Red]/media   [/COLOR]     ext4 users,user,owner                    0  2  
If the FAT partition has issues, I might try using a Windows repairCD and run chkdsk.

I do not like using names like sda6 as a mount but something better like your mount of 'storage'. That may be why it is giving issues as you are trying to directly mount it. 

# Make permanent mount point (unmount if already mounted):
[COLOR=Red]sudo mkdir /media/storage[/COLOR]
# Find your UUID:
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

You can edit existing to be like this, if UUID is correct:
> # /storage was on /dev/sdb7 during installation
UUID=a38b17fc-5601-42f5-9484-462c6d59f231  [COLOR=Red]/media/storage   [/COLOR]     ext4 relatime                   0  2  


# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

---

### Post by theheadlessrabbit on 2012-02-01
The fat partition is completely empty right now (it's a new freshly built machine, nothing important is on it now, so just giving up and doing a full re-install wouldn't hurt that much).  

I tried reformatting the FAT32 partition in Gparted, just to see if that would help at all.  No luck.

---

### Post by oldfred on 2012-02-02
Better to use NTFS anyway if you have no data to save.

FAT does not have  a journal and cannot store files over 4GB.

---

### Post by strobon on 2012-05-02
@theheadlessrabbit, can you share what the switch in ubuntu to install.i have the same Motherboard GA Z68XP UD4.try to boot Ubuntu 11.10 but can't boot to installer menu.thx in advance

sorry bad english.

---

