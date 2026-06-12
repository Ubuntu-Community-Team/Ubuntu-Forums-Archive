---
title: "Recover data from a failed Vista HDD"
date: 2009-11-15
forum: General Help
---

### Post by MartynT on 2009-11-15
Hi,
it might seem odd asking an ubuntu forum for help with a "vista" disk, but I know you're a friendly lot.

My wife's vista laptop is now failing to boot.  I've tried a raft of vista recoveries all to no avail so no I'm thinking of using ubuntu to just recover some data (emails, photos, etc.).

I'm pretty sure it's a HDD problem, rather than memory (I'm typing this from UNR 9.04 live on a usb stick).
The HDD has 2 partitions.  The 2nd is fully accessible from ubuntu but the first wont mount.  It appears as a "place" in Nautilus, but when clicked gives a Cannot Mount popup.

There's a long error message ... 

ntfs_mst_post_read_fixup: Invalid argument Record 10 has no FILE magic (0x1) Failed to open inode FILE_UpCase: Input/output error Failed to mount '/dev/sda2' .... etc.

Is [http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/) what I need ?

Any other advice greatly appreciated.

---

### Post by aysiu on 2009-11-16
I would use *photorec* to recover the data.

More details here:
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles](http://www.psychocats.net/ubuntucat/recoverdeletedfiles)

---

### Post by Giblet5 on 2009-11-16
Try fixing it with ```
sudo ntfsfix /dev/sdXX
```

Where XX is the drive partition.

The structure is corrupted and until you fix it, you won't be able to boot it or mount it.

---

