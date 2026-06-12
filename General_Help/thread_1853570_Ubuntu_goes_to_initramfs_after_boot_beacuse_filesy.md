---
title: "Ubuntu goes to initramfs after boot beacuse filesystem is not clean"
date: 2011-10-02
forum: General Help
---

### Post by johncoss on 2011-10-02
Hi,

I am using Ubuntu 10.10 half a year and recently it wont boot normally. GRUB2 is loading nicely and allows me to choose installed Operating systems. Win7 loads just fine.
However, when I choose Ubuntu it presents me with some messages and prompt that says initramfs.
Did a bit of research online and someone suggested that ext4 filesystem might be corrupted (although it might prove wrong). I booted system with Ubuntu LiveCD and run Disk utility to check my disks. All partitions seems fine, except /dev/sda15 which is root of Ubuntu. Check Filesystem option reports that file system is NOT clean.
I read that in this case you must unmount root filesystem and run e2fsck to fix partition.
However I was not able to fix partition. Here is terminal output:

```
ubuntu@ubuntu:~$ sudo umount /dev/sda15
umount: /dev/sda15: not mounted
ubuntu@ubuntu:~$ sudo e2fsck -f -v /dev/sda15
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda15
Filesystem mounted or opened exclusively by another program?
```Umount command fails since root is not mounted, which is fine with me since root filesystem is not mounted in liveCD. e2fsck fails reporting that fs is mounted or opened exclusively.

What should I do now?

Thanks.

---

### Post by prodigy_ on 2011-10-02
Interesting. What do ```
sudo file -sL /dev/sda15
sudo fdisk -l
``` say?

---

### Post by johncoss on 2011-10-02
Hi Prodigy_,

Sry for a late response (had to reboot system to linux)

Here is the output of commands you gave me:
```
ubuntu@ubuntu:~$ sudo file -sL /dev/sda15
/dev/sda15: Linux rev 1.0 ext4 filesystem data, UUID=8a095b67-2b07-4e3a-b3fe-79880160ccc0 (needs journal recovery) (errors) (extents) (large files) (huge files)
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdabd54cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223       14360    73400985    7  HPFS/NTFS
/dev/sda3           14361      121602   861415125+   f  W95 Ext'd (LBA)
/dev/sda5           14361       19582    41945683+   7  HPFS/NTFS
/dev/sda6           19583       32636   104856223+   7  HPFS/NTFS
/dev/sda7           32637       45690   104856223+   7  HPFS/NTFS
/dev/sda8           45691       58744   104856223+   7  HPFS/NTFS
/dev/sda9           58745       71798   104856223+   7  HPFS/NTFS
/dev/sda10          71799       80936    73400953+   7  HPFS/NTFS
/dev/sda11          80937      116182   283113463+   7  HPFS/NTFS
/dev/sda12         116183      116669     3905536   82  Linux swap / Solaris
/dev/sda13         116669      116681       96256   83  Linux
/dev/sda14         116681      119112    19529728   83  Linux
/dev/sda15         119113      121602    19994624   83  Linux

```Thank you for your interest.

---

### Post by prodigy_ on 2011-10-02
Check this bug:
[https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/656526](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/656526)

You might want to use a different LiveCD because e2fsck on 10.10 LiveCD appears to be broken.

---

### Post by johncoss on 2011-10-03
Thanks for your reply. I will try with 10.04 or 9.10 version of ubuntu liveCD to see what happens. I will test this when I come from work and I will post my findings.

Thanks again!

---

### Post by johncoss on 2011-10-03
Yes! You were right.
Ubuntu 10.10 LiveCD contain faulty e2fsck tool. I used Ubuntu 9.10 LiveCD and it fixed my root filesystem in a second.
Now GRUB boots Ubunutu correctly.

Thanks for your help.

---

