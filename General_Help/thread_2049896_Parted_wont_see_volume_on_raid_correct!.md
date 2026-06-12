---
title: "Parted wont see volume on raid correct?!"
date: 2012-08-29
forum: General Help
---

### Post by andolf on 2012-08-29
Hello!
I recently expanded my raid from 4TB to 6TB, and my raidcard is just finished both migrating and resizing the RAID. (ARECA ARC-1260 with RAID-5). Please help me expand my parted volume and filesystem!!

Output:
```

root@ubuntu:~# resize2fs /dev/sdb1
resize2fs 1.42 (29-Nov-2011)
The filesystem is already 976562423 blocks long.  Nothing to do!

root@ubuntu:~#

```


```
root@ubuntu:~# parted /dev/sdb1
GNU Parted 2.3
Using /dev/sdb1
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s
(parted) print
Model: Unknown (unknown)
Disk /dev/sdb1: 7812499389s
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End          Size         File system  Flags
 1      0s     7812499388s  7812499389s  ext4

(parted)

```

```
root@ubuntu:~# parted /dev/sdb1
GNU Parted 2.3
Using /dev/sdb1
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: Unknown (unknown)
Disk /dev/sdb1: 4000GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  4000GB  4000GB  ext4

(parted)

```

```
     &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
     &#9474;  Main Menu                &#9474;
     &#9500;&#9472;&#9472;&#9472;&#9472;&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
     &#9474;  Qu&#9474;  Volu&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
     &#9474;  Ra&#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9474;  The Volume Set Information                &#9474;
     &#9474;  Vo&#9474;  Crea&#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508;&#9488;
     &#9474;  Ph&#9474;  Dele&#9474;  Volume Set Name : WD2TB                   &#9474;&#9474;
     &#9474;  Ra&#9474;  Modi&#9474;  Raid Set Name   : WD2TB                   &#9474;&#9508;
     &#9474;  Hd&#9474;  Chec&#9474;  Volume Capacity : 6000.0GB                &#9474;&#9474;
     &#9474;  Et&#9474;  Stop&#9474;  Volume State    : Normal                  &#9474;&#9474;
     &#9474;  Vi&#9474;  Disp&#9474;  SCSI Ch/Id/Lun  : 0/0/1                   &#9474;&#9496;
     &#9474;  Cl&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9474;  RAID Level      : 5                       &#9474;
     &#9474;  Hardware &#9474;  Stripe Size     : 128 KB                  &#9474;
     &#9474;  System In&#9474;  Block Size      : 512 Bytes               &#9474;
     &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9474;  Member Disks    : 4                       &#9474;
                 &#9474;  Cache Attribute : Write-Through           &#9474;
                 &#9474;  Tag Queuing     : Enabled                 &#9474;
                 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;


```

How can this be? Please help!

---

