---
title: "To mount an existing partition in System"
date: 2011-10-04
forum: General Help
---

### Post by guru boy on 2011-10-04
Hi all,
I had my 160 GB HDD partitioned into 120 and 40 GB for ubuntu and windows respectively about 2 years ago,
I stopped using windows as time passed, now i want to use that 40 GB partition, so I formatted it using ubuntu's 'Partition Editor' utility, but still I am unable to use that partition, it is showing in start menu as a separate disk, and with sudo user it is impossible to use that disk.
please tell me how to add that partition as a regular partition of my ubuntu installation.
I am using ubuntu 8.10

---

### Post by seawolf167 on 2011-10-04
First things first, I'd suggest upgrading from 8.10 as it is no longer supported and has reached its [end of life ]("https://wiki.ubuntu.com/Releases")(April 30th, 2010!)

As for your question - are you trying to have it mounted automatically as a separate file system, or are you trying to have it "become one" (merge) with the current / (root) or /home partitions?

---

### Post by garvinrick4 on 2011-10-04
> **guru boy said:**
> Hi all,
I had my 160 GB HDD partitioned into 120 and 40 GB for ubuntu and windows respectively about 2 years ago,
I stopped using windows as time passed, now i want to use that 40 GB partition, so I formatted it using ubuntu's 'Partition Editor' utility, but still I am unable to use that partition, it is showing in start menu as a separate disk, and with sudo user it is impossible to use that disk.
please tell me how to add that partition as a regular partition of my ubuntu installation.
I am using ubuntu 8.10 
You should see the partition:
```
sudo fdisk -l
``` (lower case L)

```
sudo parted -l
```(lower case L)

Post the results of these 2 to see what is there. Can auto mount using fstab if all is ok with partition table.
Should show up on left side of nautilus window as a partition.
Or mount in /mnt at any given time.

Beow is in fstab to automount.
```
gksudo /etc/fstab
``` 
and just added to bottom of file (use your sda# , UUID, and name /media/whatever)
sudo blkid (lower case L) to get UUID
```

# /dev/sda7
UUID=0f7c5de9-c3b4-4c50-b288-d34e9ef6e119 /media/data      ext4   defaults    0

```NTFS format below
```
# /dev/sda8
UUID=1927A02F2C3A884A /media/data  ntfs-3g defaults,user,locale=en_US.utf8 0 0
```
##Sh[COLOR=Red]ow the output of 2 commands given above if you want to be safe.[/COLOR]

---

