---
title: "Command line partition editor"
date: 2011-02-19
forum: General Help
---

### Post by towheedm on 2011-02-19
I have a 500G HD with several partitions.  I have just added another exact 500G HD and would like to copy the partition table from the first HD to the new HD.

What is a good command line partition editor to get the job done?  All of my partitions are ext4.  I have looked at parted but the man pages says it does not support ext3, so I guess it will not work with ext4 either.

What I am ultimately going to do is to set these two HD in a RAID0 configuration without having to re-install Karmic.

Thanks.

---

### Post by dino99 on 2011-02-19
asked our google friend:

[http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk](http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk)

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

[http://dimitar.me/clone-disk-drives-with-ubuntu/](http://dimitar.me/clone-disk-drives-with-ubuntu/)

and so on

---

### Post by towheedm on 2011-02-19
Thanks, will have a look at the links.

---

### Post by HermanAB on 2011-02-19
Goodness me.  Just use fdisk to display the partitions on the old disk and then make new partitions on the new disk.

---

### Post by srs5694 on 2011-02-20
The question is confounding two very different issues:


[list]
[*]Copying the partition table
[*]Copying the filesystems
[/list]


The partition table defines where partitions begin and end along with various other types of information. The partition table does *not* include any data (files) stored in the partitions. The partition table can be copied as HermanAB suggests, or by using sfdisk, as in:

```

$ **sudo sfdisk -d /dev/sda > parts.txt**
$ **sudo sfdisk /dev/sdb < parts.txt**

```

These two commands, taken together, will copy the partition table from /dev/sda to /dev/sdb; but these commands (or using fdisk and manually copying the data) will not copy the contents of the filesystems. For that, you'll need to either add several more commands (to create filesystems and copy all the files, say by using mkfs and tar) or use a tool such as Clonezilla to copy the whole disk.

All this said, the ultimate goal of converting the disk from a conventional configuration to a RAID 0 configuration will not be served by any of these procedures. Offhand, I'm not sure of how to convert existing partitions into a RAID 0 setup. It may not be possible at all, at least not with the standard utilities. My own suggestion would be to back up, create the RAID 0 configuration, and then restore. (Personally, I'd use LVM rather than RAID, but that's another matter. Using LVM would permit conversion without the need for a separate backup medium, although striping options would then be limited.)

---

### Post by towheedm on 2011-02-20
> **srs5694 said:**
> 

All this said, the ultimate goal of converting the disk from a conventional configuration to a RAID 0 configuration will not be served by any of these procedures. Offhand, I'm not sure of how to convert existing partitions into a RAID 0 setup. It may not be possible at all, at least not with the standard utilities. My own suggestion would be to back up, create the RAID 0 configuration, and then restore. (Personally, I'd use LVM rather than RAID, but that's another matter. Using LVM would permit conversion without the need for a separate backup medium, although striping options would then be limited.)

Yes, I wanted to copy the partition layout and not the data.  I did use:

```
sfdisk -d /dev/sdb | sfdisk /dev/sdc
```
which copy the layout.  And you are correct, I did backup, create the raid0 partitions and am in the process of restoring my original files to the raid 0 partitions.  Of course there a few more steps after the restore to get the original OS to work with RAID 0 partitions.

---

