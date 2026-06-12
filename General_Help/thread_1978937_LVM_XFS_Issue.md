---
title: "LVM XFS Issue"
date: 2012-05-12
forum: General Help
---

### Post by kentish on 2012-05-12
Hi 

If anyone can shed some light on my current issue I will will really greatful. 

I have an server with an LVM with two volume groups - Data and Video, Data is one drive and Video is three (2tb + 1tb + 1tb) yesterday night I check syslog and saw a load of these errrors.

[LIST]
[*]Unhandled Sense code 
[*]Failed read FPDMA queued
[*]Exception Emask frozen
[/LIST]

The video share disappeared so powered it down (which might of been a mistake) Booted into a live ubuntu session and started checking the drives.

Data volume group is fine and I mount and retrieve all the information from here, so no worries there.

However video is presenting issues...

Disk utility says that 

Device		Smart Data 
1TB		Disk is Healthy
500gig		Disk is Healthy
1TB		Disk is Healthy
2TB		Disk has a few bad sectors (1 bad sector)

So I have tried ```
vgscan -a y
``` to active the volume groups and then tried

```
sudo xfs_check /dev/mapper/Media-Video 
```and ```
sudo xfs_check /dev/dm-3
``` both return
```
xfs_check: /dev/mapper/Media-Video is invalid (cannot read first 512 bytes)
```

```
sudo xfs_check /dev/sdd
``` returns
```
xfs_check: /dev/sdd is not a valid XFS filesystem (unexpected SB magic number 0x00000000)
xfs_check: WARNING - filesystem uses v1 dirs,limited functionality provided.
xfs_check: read failed: Invalid argument
xfs_check: data size check failed
cache_node_purge: refcount was 1, not zero (node=0xdf0090)
xfs_check: cannot read root inode (22)
bad superblock magic number 0, giving up
```


After which I tried
then tried ```
xfs_check -n /dev/sdd 
``` and ```
xfs_repair -n /dev/mapper/Media-Video
``` and finally ```
xfs check -n /dev/dm-3
```

All fail with Fatal Error - Input / Output Error

I hope that's enough information as I am not sure what else to tried.

Thanks 


Mark

---

### Post by SeijiSensei on 2012-05-12
This might not be the news you want to hear, but my experience with XFS and loss of power has been terrible.  I had an external drive with an XFS filesystem, and if the power went out, I either lost a large chunk of recent files or had worse corruption.  Now I just use ext4.

---

### Post by kentish on 2012-05-12
Yup your right that's not the news I want although I am coming to the conclusion that 3.5 TB of data has just gone. So now just waving good bye ):P to it!

---

