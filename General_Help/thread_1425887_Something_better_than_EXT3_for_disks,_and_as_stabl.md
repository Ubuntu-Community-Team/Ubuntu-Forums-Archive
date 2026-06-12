---
title: "Something better than EXT3 for disks, and as stable as NTFS Windows Microsoft?"
date: 2010-03-09
forum: General Help
---

### Post by frenchn00b on 2010-03-09
Hello,

I never had so much crashes of harddisks than with LINUX. NTFS, when I had windows XP, never crashed and I never lost any data.

EXT3 it crashes every once a year, badly, and **** all your data. I mean that cant be like that. I do lot of tiny files... as I was doing under windows.

So EXT3 is not to be recommended. What is better and working under LINUX well? Is the BSD better, less crashing paritions/disks?

I note that all my disks are under:
tunefs -c 2 
count 2 and this doesnt help much, well a bit... of Debian/Ubuntu are releasing really crashign util-linux ... 

I do not know more, just it crashes and windows never !!

---

### Post by doas777 on 2010-03-09
ummmm, disks don't crash, in a filesystem sense. a "head crash" is a hardware problem, and has nothing to do with what software filesystem you use.

so are you saying your filesystem has become unusably corrupted? perhaps due to a power failure? I have never had that issue in linux (though I have had it several times in windows on NTFS).

you may want to try ext4 and turn on journaling mode, so that you can recover transactions that are not fully committed or rollback as needed. it may help next time you do have a kernel panic or a power fail. 

I've been hearing a bit about ButterFS (BRFS I think), but have heard that it is not quite ready for deployment, and there are always the AndrewFS and ReiserFS/MurderFS.

---

### Post by ubudog on 2010-03-09
Maybe try ext4.  Been pretty stable.

---

### Post by cjhabs on 2010-03-09
Just reading this thread out of interest - I am using ext4 - I thought that ext4 had journaling turned on by default - that it actually was ext3 + journaling. Am I misinformed? How can I check that I have journaling turned on?

Thanks

---

### Post by doas777 on 2010-03-09
> **cjhabs said:**
> Just reading this thread out of interest - I am using ext4 - I thought that ext4 had journaling turned on by default - that it actually was ext3 + journaling. Am I misinformed? How can I check that I have journaling turned on?

Thanks
actually neither used journaling by default unless you turn them on. both use "Data" mode.

---

### Post by cjhabs on 2010-03-09
I am confused now - I didn't do anything to enable journaling when building my system. Running "sudo dumpe2fs /dev/sda6" gives:
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize

Does "has_journal" mean that it is using journaling - or should I check another way?

---

### Post by dcstar on 2010-03-09
> **doas777 said:**
> actually neither used journaling by default unless you turn them on. both use "Data" mode.

EXT3 is EXT2 with "Journaling", EXT4 is an advance on EXT3 and certainly uses journaling as default.

---

### Post by efflandt on 2010-03-09
I have been running Linux since at least 1995, and have had hard drives fail, but never catastrophic or any data lost under Linux.  Usually fsck gave clues that there were problems, typically when I got farther into a disk where I think the sectors were physically smaller (data more packed together) and more difficult to read.  I thought I had been using ext3, but in the earlier days it was apparently ext2, and reiser during the SuSE 8.0 to 8.2 days some time ago.  An example of a monitorless Celeron 300 that has not been shutdown for over 3 years:

```
> mount
/dev/hda2 on / type reiserfs (rw)
proc on /proc type proc (rw)
devpts on /dev/pts type devpts (rw,mode=0620,gid=5)
/dev/hda3 on /usr/archive type reiserfs (rw)
/dev/hdb1 on /mnt/hdb1 type ext2 (rw)
/dev/hdb2 on /mnt/hdb2 type ext2 (rw)
/dev/hdb4 on /mnt/hdb4 type ext2 (rw)
shmfs on /dev/shm type shm (rw)
usbdevfs on /proc/bus/usb type usbdevfs (rw)

> ls -l /var/log/*boot*
-rw-r-----    1 root     root            0 2003-05-17 18:03 /var/log/boot.log
-rw-r--r--    1 root     root        20461 2006-07-20 16:00 /var/log/boot.msg
-rw-r--r--    1 root     root        24670 2006-07-20 04:45 /var/log/boot.omsg

> cat /etc/*-release
SuSE Linux 8.2 (i586)
VERSION = 8.2

> cat /mnt/hdb1/etc/*-release
Linux Mandrake release 7.0 (Air)
Linux Mandrake release 7.0 (Air)

And my archive partition:
> ls -l /mnt/hdb4
total 56
drwxr-xr-x    5 root     root         4096 2001-11-21 21:19 SuSE7.1
drwxr-xr-x    5 root     root         4096 2001-12-01 18:37 SuSE7.1lap
drwxr-xr-x    5 root     root         4096 2002-01-12 11:31 SuSE7.3
drwxr-xr-x    6 root     root         4096 2002-08-21 04:16 SuSE7.3b
drwxr-xr-x    5 root     root         4096 2002-09-07 14:03 SuSE7.3lap
drwxr-xr-x    2 root     root         4096 2002-01-13 17:25 kernels
drwxr-x---    6 501      503          4096 2001-03-03 12:04 laptop-mdk
drwxr-xr-x    2 root     root         4096 2003-11-12 19:08 lost+found
drwxr-xr-x    6 501      503          4096 2001-03-12 23:03 pictures
drwxr-xr-x    3 root     root         4096 2000-09-23 23:52 redhat6.1
drwxr-xr-x    4 root     root         4096 2001-11-21 21:32 slack8
drwxr-xr-x    2 root     root         4096 2001-11-10 18:36 source
drwxr-xr-x    4 root     root         4096 2003-05-17 10:36 tmpfiles
drwxr-xr-x    2 1001     1001         4096 2000-09-23 20:41 video
```My BIOS gave me fair warning when a the Win98se drive that came in an out of the box returned K6/2-400 PC I bought for $100.00 at Best Buy was about to fail.  One boot it said "imminent drive failure" and on the next boot, it did.  I just unplugged that drive and made my Linux drive the master boot drive (with LILO at that time).  That was the only drive I had fail suddenly and completely, but it had been making clicking sounds like it was having read issues for months before that.

---

### Post by cjhabs on 2010-03-10
> **dcstar said:**
> EXT3 is EXT2 with "Journaling", EXT4 is an advance on EXT3 and certainly uses journaling as default.

Thanks for the clarification.

---

