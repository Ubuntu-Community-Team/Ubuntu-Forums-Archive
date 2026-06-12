---
title: "wubi - kernel panic - unable to mount root.disk"
date: 2009-12-16
forum: General Help
---

### Post by amanjain on 2009-12-16
Hi

 We all of a sudden faced a kernel panic upon booting into wubi's Ubuntu 9.10, without any reason.

Message:
"Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(2,0)"

Now, we want to at least recover our data(if not boot into wubi's ubuntu 9.10 again). 
After seeing a related post at [https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide") "How can I access my Wubi install and repair my install if it won't boot?"

we tried 
$ sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Here is the output produced by dmesg:
$ dmesg
[ 4270.353169] EXT4-fs: barriers enabled
[ 4270.353479] JBD: no valid journal superblock found
[ 4270.353493] EXT4-fs: error loading journal.

Result of 'fsck':
# fsck.ext4 /mnt/wubi/disks/root.disk 
e2fsck 1.41.4 (27-Jan-2009)
/mnt/wubi/disks/root.disk: clean, 189853/1073152 files, 1999372/4286464 blocks
# fsck /mnt/wubi/disks/root.disk
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/mnt/wubi/disks/root.disk: clean, 189853/1073152 files, 1999372/4286464 blocks

Result of 'file' command:
# file /mnt/wubi/disks/root.disk
/mnt/wubi/disks/root.disk: Linux rev 1.0 ext4 filesystem data, UUID=9e666ee0-645-48fb-95fc-f407e7b99ed8 (extents) (large files) (huge files)

Any help on recovering our data would be much appreciated.

TIA
Aman Jain

---

### Post by Kr4bat on 2009-12-17
There have been 2 Solution, which i found an will try out tomorrow: - boot live System, do mkinitramfs to make a new initramfs,   (backup old!) change grub.cfg to point on new initramfs - create new bootdisk with ext2, copy data, write Grub MBR,   change grub.cfg to point on new boot.disk  Booting the old Kernel (if you have it still there), solved the problem in the meantime, so i could still work on...

---

