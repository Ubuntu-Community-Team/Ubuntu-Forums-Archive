---
title: "Creating a new partition SOLEY for music"
date: 2006-02-16
forum: General Help
---

### Post by jrattner on 2006-02-16
My current set up is flawed to the extent that everytime I do a fresh install on linux, I loose all of my music.  What I'm trying to do is find the easiest way to create a partition that I can keep my music on seperately, so I don't loose it each time I do a fresh install.  I'm looking for this partiton to automount, and am curious if this is a simple seemless process, or something that is long and involved.

sudo fdisk -l reports the following: 
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4092    32868958+   7  HPFS/NTFS
/dev/hda2            4093        9496    43407630   83  Linux
/dev/hda3            9497        9729     1871572+   f  W95 Ext'd (LBA)
/dev/hda5            9497        9729     1871541   82  Linux swap / Solaris

```

Any help would be appreciated.

---

### Post by Vanquirius on 2006-02-16
It should be a simple matter of creating the partition, formatting it with a file system (like reiserfs or ext3) and adding an entry for it in /etc/fstab.

---

### Post by chaumurky on 2006-02-16
Install gparted as you'll need to resize the linux partition to create some space for the new one. Create the new partition in the free space and make note of the device name that's created i.e. /dev/hd? (? is the number you need to note). I'd use ext3 for your new partition becase you can resize it later if you need to. As root, create a new folder to which you will mount the new partition (I use /media/music as it shows on my desktop). Then add the entry to /etc/fstab. Something like **/dev/hdc? /media/music ext3 noatime 0 2** When that's done go** sudo mount -a** Copy your music in there and you're done. If you ever reinstall just set the mount option during the install to /media/music or whatever. Hope this helps.

---

