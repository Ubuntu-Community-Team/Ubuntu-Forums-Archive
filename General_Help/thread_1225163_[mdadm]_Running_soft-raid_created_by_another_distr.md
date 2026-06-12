---
title: "[mdadm] Running soft-raid created by another distro"
date: 2009-07-28
forum: General Help
---

### Post by Dinth on 2009-07-28
Ive recently installed Ubuntu on my machine (earlier it was running Arch linux). In Arch i have been using soft-raid (raid0) partition as my /home directory. Unfortunately, i cannot force Ubuntu to mount this partition.

I do 
```

dinth@dinth-desktop-ubuntu:~$ sudo mdadm --assemble --scan
mdadm: /dev/md/0 has been started with 2 drives.

```
```

inth@dinth-desktop-ubuntu:~$ cat /proc/mdstat
Personalities : [raid0] 
md0 : active raid0 sda3[0] sdb2[1]
      867718816 blocks super 1.0 32k chunks

```

Thats ok. Soft raid should be created from /dev/sda3 and /dev/sdb2.

But:
```

dinth@dinth-desktop-ubuntu:~$ sudo mount -t ext4 /dev/md/0 /home2
mount: wrong fs type, bad option, bad superblock on /dev/md/0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dinth@dinth-desktop-ubuntu:~$ dmesg | tail
[  210.594893] raid0: zone->nb_dev: 1, size: 16787936
[  210.594894] raid0: current zone offset: 442253376
[  210.594896] raid0: done.
[  210.594897] raid0 : md_size is 867718816 blocks.
[  210.594898] raid0 : conf->hash_spacing is 850930880 blocks.
[  210.594900] raid0 : nb_zone is 2.
[  210.594901] raid0 : Allocating 16 bytes for hash.
[  210.595076]  md0: unknown partition table
[  219.106048] ext4: No journal on filesystem on md0
[  225.820098] ext4: No journal on filesystem on md0

```
When i was reinstalling Arch linux some time ago, i got similar problem (with finding valid partition table on /dev/md0) when i've tried to assemble my software raid on Live-CD, but problem magically disappeared when ive booted installed system. Here on Ubuntu, unfortunately problem exists both on Live-CD and installed system :(

```

dinth@dinth-desktop-ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c1e7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2         523     4192965   82  Linux swap / Solaris
/dev/sda2   *         524        5743    41929650    7  HPFS/NTFS
/dev/sda3            5744       60801   442253385   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007c98b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7833    62918541   83  Linux
/dev/sdb2            7834       60801   425465460   fd  Linux raid autodetect

Disk /dev/md0: 888.5 GB, 888544067584 bytes
2 heads, 4 sectors/track, 216929704 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

---

### Post by Dinth on 2009-07-28
Strange is that fsck sees proper filesystem but mount dont.
```
dinth@dinth-desktop-ubuntu:/usr/share/man$ sudo fsck.ext4 -f /dev/md/0
e2fsck 1.41.4 (27-Jan-2009)
Przebieg 1: Sprawdzanie i-w&#281;z&#322;ów, bloków i rozmiarów
Przebieg 2: Sprawdzanie struktury katalogów
Przebieg 3: Sprawdzanie &#322;&#261;czno&#347;ci katalogów
Przebieg 4: Sprawdzanie liczników odwo&#322;a&#324;
Przebieg 5: Sprawdzanie sumarycznych informacji o grupach
/dev/md/0: 634231/54239232 plików (8.2% nieci&#261;g&#322;ych), 156993222/216929704 bloków
dinth@dinth-desktop-ubuntu:~$ sudo mount /dev/md/0 /home2
mount: you must specify the filesystem type

```

also tune2fs sees filesystem.

```
dinth@dinth-desktop-ubuntu:~$ sudo tune2fs -l /dev/md/0
tune2fs 1.41.4 (27-Jan-2009)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          a13a3649-f249-49e1-98de-c48ce5072acf
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              54239232
Block count:              216929704
Reserved block count:     10846485
Free blocks:              59936482
Free inodes:              53605001
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      972
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Fri Mar  6 17:59:57 2009
Last mount time:          Tue Jul 28 07:34:19 2009
Last write time:          Tue Jul 28 20:31:16 2009
Mount count:              0
Maximum mount count:      34
Last checked:             Tue Jul 28 20:31:16 2009
Check interval:           15552000 (6 months)
Next check after:         Sun Jan 24 19:31:16 2010
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Default directory hash:   half_md4
Directory Hash Seed:      e9081992-a3ac-4624-a4c5-f7083f70f415
Journal backup:           inode blocks

```

---

### Post by jmcboots on 2009-08-02
I have the same problem. On my /home directory.

I have a two drive raid /dev/md0.
I have LVM setup on top of that at /dev/homevg/homelv
Which is formated with ext4.

$ sudo lvscan
  ACTIVE            '/dev/homevg/homelv' [1.36 TB] inherit

$ sudo fsck.ext4 -p /dev/homevg/homelv
/dev/homevg/homelv: clean, 1336754/91578368 files, 183884442/366283776 blocks

$ sudo mount -t ext4 /dev/homevg/homelv /home
mount: wrong fs type, bad option, bad superblock on /dev/mapper/homevg/homelv,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When I check dmesg I get:
ext4: No journal on filesystem on dm-0

It appears that I have lost the journal somehow. Can that be right?

How can I fix this?

---

### Post by Dinth on 2009-08-04
Manualy building new journal by tune2fs helped me.

---

