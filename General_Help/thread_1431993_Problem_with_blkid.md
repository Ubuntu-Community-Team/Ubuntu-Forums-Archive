---
title: "Problem with blkid"
date: 2010-03-17
forum: General Help
---

### Post by dnoyeb on 2010-03-17
When I issue the blkid command I am getting varying results.

First time I got this (note xb3/xa3 and xb4/xa4 xb5/xa5 have same uuid)

```
carl@erasmus:~$ blkid
/dev/sda1: UUID="e9291a53-218d-e704-468a-b3063828ac7e" TYPE="mdraid"
/dev/mapper/VolumeOne-home: UUID="38c94a76-d832-413c-8db3-3e9cd3aa0a16" SEC_TYPE="ext2" TYPE="ext3"
/dev/mapper/VolumeOne-shared: UUID="9e802821-fa23-407b-8f2c-4e3b8167605d" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb1: UUID="2a5c4a3e-3433-41a1-84eb-ffe0afdca0c4" TYPE="ext3"
/dev/md0: UUID="dae9629b-76a3-4afa-9dd5-3d693b29dbf9" TYPE="ext2"
/dev/sdb3: UUID="82468fda-14b3-44b5-9467-1eb3d00148ac" TYPE="ext3" SEC_TYPE="ext2"
/dev/sdb5: TYPE="swap" UUID="7a40fa84-696e-4f4f-b4a1-85d3a88ca330"
/dev/sda3: UUID="82468fda-14b3-44b5-9467-1eb3d00148ac" TYPE="ext3" SEC_TYPE="ext2"
/dev/sda5: TYPE="swap" UUID="7a40fa84-696e-4f4f-b4a1-85d3a88ca330"
/dev/sdb4: UUID="9b23d76e-5adf-4fbf-9591-c172ac98d48d" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda4: UUID="9b23d76e-5adf-4fbf-9591-c172ac98d48d" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb6: UUID="Wkn6De-2zpm-ExeW-XaD3-H4dW-lpu6-iY8rRw" TYPE="lvm2pv"
```

Subsequent executions yielded this:

```
carl@erasmus:~$ blkid
/dev/sda1: UUID="e9291a53-218d-e704-468a-b3063828ac7e" TYPE="mdraid"
/dev/mapper/VolumeOne-home: UUID="38c94a76-d832-413c-8db3-3e9cd3aa0a16" SEC_TYPE="ext2" TYPE="ext3"
/dev/mapper/VolumeOne-shared: UUID="9e802821-fa23-407b-8f2c-4e3b8167605d" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb1: UUID="2a5c4a3e-3433-41a1-84eb-ffe0afdca0c4" TYPE="ext3"
/dev/md0: UUID="dae9629b-76a3-4afa-9dd5-3d693b29dbf9" TYPE="ext2"
/dev/sdb3: UUID="df1c55c0-1e18-44c9-a79e-c6952f4e941a" TYPE="ext3" SEC_TYPE="ext2"
/dev/sdb5: TYPE="swap" UUID="921ee2b6-d2f4-454f-a71a-af7c32ed00ba"
/dev/sda3: UUID="82468fda-14b3-44b5-9467-1eb3d00148ac" TYPE="ext3" SEC_TYPE="ext2"
/dev/sda5: TYPE="swap" UUID="7a40fa84-696e-4f4f-b4a1-85d3a88ca330"
/dev/sdb4: UUID="9b23d76e-5adf-4fbf-9591-c172ac98d48d" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda4: UUID="9b23d76e-5adf-4fbf-9591-c172ac98d48d" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb6: UUID="Wkn6De-2zpm-ExeW-XaD3-H4dW-lpu6-iY8rRw" TYPE="lvm2pv"
```


Note sdb3
First its
/dev/sdb3: UUID="df1c55c0-1e18-44c9-a79e-c6952f4e941a" TYPE="ext3" SEC_TYPE="ext2"
Then its
/dev/sdb3: UUID="82468fda-14b3-44b5-9467-1eb3d00148ac" TYPE="ext3" SEC_TYPE="ext2"

note sdb5 swap
first its (which is same as sda5 but /dev/sda5 does not exist from fdisk)
/dev/sdb5: TYPE="swap" UUID="7a40fa84-696e-4f4f-b4a1-85d3a88ca330"
Then its
/dev/sdb5: TYPE="swap" UUID="921ee2b6-d2f4-454f-a71a-af7c32ed00ba"

Finally, sdb4 and sda4 are just the same and stay that way.
/dev/sdb4: UUID="9b23d76e-5adf-4fbf-9591-c172ac98d48d" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda4: UUID="9b23d76e-5adf-4fbf-9591-c172ac98d48d" SEC_TYPE="ext2" TYPE="ext3"


for reference see my fdisk
```
carl@erasmus:~$ sudo sfdisk -l
[sudo] password for carl:

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  38912   38913- 312568641   fd  Linux raid autodetect
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty

Disk /dev/sdb: 152626 cylinders, 64 heads, 32 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: The partition table looks like it was made
  for C/H/S=*/255/63 (instead of 152626/64/32).
For this listing I'll assume that geometry.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+   1663    1664-  13366048+  83  Linux
/dev/sdb2       5099+  19457-  14359- 115332131+   5  Extended
/dev/sdb3       1664    3320    1657   13309852+  83  Linux
/dev/sdb4       3321    5098    1778   14281785   83  Linux
/dev/sdb5       5099+   5226     128-   1028128+  82  Linux swap / Solaris
/dev/sdb6       5227+  19457-  14231- 114303971   8e  Linux LVM
```

"sda" is a single drive setup in software RAID.
"sdb" is 2 drives connected to a 3ware RAID-1 and appear as a single drive.


1. How can UUIDs keep changing during 1 SSH session?
2. How can seperate partitions have the same UUID?

---

### Post by dnoyeb on 2010-03-18
Any info or should I file a bug report on this?

I'm using Ubuntu 9.4.

---

### Post by john newbuntu on 2010-03-19
To avoid a bad cache file, does running the following yield something consistent:
sudo blkid -c /dev/null

---

