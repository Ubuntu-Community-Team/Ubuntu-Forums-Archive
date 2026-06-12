---
title: "Issue mounting ext4 partition"
date: 2010-09-08
forum: General Help
---

### Post by xail on 2010-09-08
Back story:
I have 2 hard drives in a striped raid (never again) and one of them is giving me real problems.  Today something went wrong and both my windows and linux partition became too corrupted to boot.  Using a live cd I was able to back up everything from the windows partition.

Problem:
I haven't been able to mount my linux partition and hopefully pull the few things off I really care about.  The partition is an ext4 partition in a LVM.

```
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/VolGroup/lv_root /mnt
mount: wrong fs type, bad option, bad superblock on /dev/mapper/VolGroup-lv_root,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

The man on mount says that ext4 is supported so I'm guessing its a super block issue. 

```
ubuntu@ubuntu:~$ sudo dumpe2fs /dev/VolGroup/lv_root 
dumpe2fs 1.41.11 (14-Mar-2010)
dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/VolGroup/lv_root
Couldn't find valid filesystem superblock.

```

Definitely something wrong with the disk, but I'm out of ideas for the moment.

---

### Post by gauravj on 2010-09-08
Hi

Only thing I can think of is

sudo mount ext4 /dev/VolGroup/lv_root /mnt -o force

see if force mount helps.

---

