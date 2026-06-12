---
title: "Expanded Array but the new size doesn't show in df"
date: 2011-06-26
forum: General Help
---

### Post by zend on 2011-06-26
I am running Ubuntu 10.04LTS (64bit) and the drives are formatted as EXT3. I have a Raid5 that had 4 x 1TB drives. It is mounted as my /home. I added a 5th Drive and used the Disk Utility to Expand the array. In the Disk Utility it shows as 4.0TB RAID5 Array, however when I open a console and type df -h it still only shows at 2.8TB (Which is the size of the 3TB array I had previously.) What do I have to do to have the 4TB array show up properly? I'm obviously missing something, but I'm not sure what it is.

---

### Post by zend on 2011-06-28
Nobody has increased the size of an RAID5 array with the disk utility and had this problem?

---

### Post by srs5694 on 2011-06-28
You need to increase the size of the filesystem (with resize2fs), and possibly the size of the partition (with GParted or various other tools) before it'll show up as the correct size. I can't be more precise in my answer without having more precise information on your setup. If you need that, please post the output from the following commands:

```

sudo parted -l
sudo df -h
sudo blkid

```

Post the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags or it will become hard to read.

---

### Post by zend on 2011-07-02
Thanks for your reply. I have been away and couldn't reply until now. Hopefully you can help me, here are the outputs for the following commands.

Note: I have a Raid1 with 2 drives (80 GB) This is my main OS.

Then I have the RAID5 with 5x1TB HDDs. That's the one I'm having the trouble with.

sudo parted -l
```

Model: ATA WDC WD1600JB-00R (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      32.3kB  80.0GB  80.0GB  primary  ext3            boot, raid
 2      80.0GB  160GB   80.0GB  primary  linux-swap(v1)


Model: ATA ST380011A (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  80.0GB  80.0GB  primary  ext3         boot, raid


Model: ATA Hitachi HDT72101 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary               boot, raid


Model: ATA Hitachi HDT72101 (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary               raid


Model: ATA ST31000528AS (scsi)
Disk /dev/sde: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary               raid


Model: ATA Hitachi HDT72101 (scsi)
Disk /dev/sdf: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary               raid


Model: Unknown (unknown)
Disk /dev/md1: 4001GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  4001GB  4001GB  ext3


Model: ATA Hitachi HDT72101 (scsi)
Disk /dev/sdg: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary               raid


Model: Unknown (unknown)
Disk /dev/md0: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  80.0GB  80.0GB  ext3

```

sudo df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/md0               74G   15G   56G  21% /
none                 1000M  336K 1000M   1% /dev
none                 1004M  544K 1004M   1% /dev/shm
none                 1004M  3.3M 1001M   1% /var/run
none                 1004M     0 1004M   0% /var/lock
none                 1004M     0 1004M   0% /lib/init/rw
/dev/md1              2.8T  1.9T  775G  71% /home

```

sudo blkid

```

/dev/sdb1: UUID="a5027528-7921-7806-0ebb-51dfc667edc3" TYPE="linux_raid_member" 
/dev/sda1: UUID="a5027528-7921-7806-0ebb-51dfc667edc3" TYPE="linux_raid_member" 
/dev/sda2: UUID="05726564-f463-455f-ac02-cfc3f430e240" TYPE="swap" 
/dev/sdc1: UUID="53d3640c-ac12-ef75-0f6e-5cf259ff89cc" TYPE="linux_raid_member" 
/dev/md1: LABEL="homedirectories" UUID="31982062-6f07-49cc-9769-a4dc538f6713" TYPE="ext3" 
/dev/sde1: UUID="53d3640c-ac12-ef75-0f6e-5cf259ff89cc" TYPE="linux_raid_member" 
/dev/sdd1: UUID="53d3640c-ac12-ef75-0f6e-5cf259ff89cc" TYPE="linux_raid_member" 
/dev/sdf1: UUID="53d3640c-ac12-ef75-0f6e-5cf259ff89cc" TYPE="linux_raid_member" 
/dev/sdg1: UUID="53d3640c-ac12-ef75-0f6e-5cf259ff89cc" TYPE="linux_raid_member" 
/dev/md0: LABEL="OSPartition" UUID="9e899cdf-21bb-47c5-82de-c84e29dbe31d" TYPE="ext3" 

```

---

### Post by zend on 2011-07-02
I'm also including a screenshot of my disk utility. Hopefully this helps as well.

[IMG]http://www.d-mystified.com/images/diskutility.png[/IMG]

---

### Post by srs5694 on 2011-07-05
Try:

```

sudo resize2fs /dev/md1

```

---

### Post by zend on 2011-07-05
It worked, and I now have 4TB of space. Thank you so much.

---

