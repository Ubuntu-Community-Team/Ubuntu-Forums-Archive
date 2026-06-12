---
title: "Mount ZFS (FreeNAS) volume in Ubuntu"
date: 2012-06-18
forum: General Help
---

### Post by CbIP on 2012-06-18
Hi all!

 I had a FreeNAS as a home server for a year. And I've collected ~450 GB of data in the last 6 months.
 But I decided to move from FreeNAS to Ubuntu. The main reason of my decision is that FreeNAS doesn't support Plex media server.
 I have one question - how to mount ZFS volume in Ubuntu to copy data from it and then to format it?

 I've already installed zfs-fuse package and tried to mount my volume: 'zpool create OldData /dev/sdb'
 It created mounting point "OldData", but 'zpool list' shows, that this mounting point has no used space. Also there are no files in /OldData.

 So, how can I mount FreeNas volume in Ubuntu?

 Thank you!

---

### Post by Velenux on 2012-06-18
I'm not an expert in ZFS, but from the man page it looks like **create** is used to, well, **create** a volume, not **mount** an existing one, so it may have zeroed out all metadata on the disk. That means your data is still somewhere on the disk, but you don't have pointers to it.

If this is the case, you may want to try PhotoRec and The Sleuth Kit to try to recover some of the files (I'm not sure they work with ZFS, tough).

---

### Post by CbIP on 2012-06-18
Looks like it was my error. I hope the data can still be recovered. My be someone here faced with the same problem and know how to solve it.
Thank you!

---

### Post by thnewguy on 2012-06-24
I think what you meant to do was perform an export/import on the data. As the above poster pointed out, the create command initializes the ZFS pool. At this point your options are probably either attempting recovery or restoring from backups.

Recovery might be difficult as I don't think most Linux tools are designed with ZFS in mind. You might try running PhotoRec on your ZFS disks. PhotoRec is available in the Ubuntu repositories. Run "sudo apt-get install testdisk" to install it.

---

### Post by Alvinator9000 on 2013-04-09
Check out this dude's stuff on ZFS for Ubuntu, read through his stuff I recall seeing somewhere about common things we humans do wrong on import/export and how to correct most problems. [http://pthree.org/2012/04/17/install-zfs-on-debian-gnulinux/](http://pthree.org/2012/04/17/install-zfs-on-debian-gnulinux/)

Also, try (once you figure out how to remove your duplicate/extra dataset):
```

zfs set mountpoint=/MyZFSVolume MyZfsPoolName

#and

zfs mount -a

```
Hopefully those two will make whatever volume you named it (change the above MyZFSPoolName) mount to location /MyZFSVolume, and then it'll mount ALL the volumes zfs sees :)

PS, sorry for being a grave digger :P

---

