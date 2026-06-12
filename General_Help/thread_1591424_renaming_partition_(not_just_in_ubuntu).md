---
title: "renaming partition (not just in ubuntu)"
date: 2010-10-09
forum: General Help
---

### Post by supermooshman on 2010-10-09
Hi all,

I would like to rename a partition on my external hard drive.
I've found quite a lot of information on the forum but most (as in all that I found) was through reconfiguring fstab.

Now I was wondering, if I change fstab, would that just change the name of the partition in ubuntu, or would it also change the name, if I mount it in Windows, or OSX?

- if there is another way of doing this for all OS, anyone could tell me how?

Thanks

---

### Post by mikewhatever on 2010-10-09
Reconfiguring fstab has nothing to do with renaming. To rename a partition, you need to change its label. Once the label is changed, all OSs that can read the file system will display it.

---

### Post by blueridgedog on 2010-10-09
You need to change the volume label.  fstab will not make persistent changes.  See for more information and commands that you can use:

[http://lissot.net/partition/ext2fs/labels.html](http://lissot.net/partition/ext2fs/labels.html)

---

### Post by clrg on 2010-10-09
That's easy. If you know what partition you want to rename (if you don't, find out with "sudo fdisk -l"), just do a:

```
sudo tune2fs -L NAME /dev/XYZ
```

---

### Post by deserthowler on 2010-10-09
You can change the label easily using gparted ... either through your desktop manager or with a live CD.  Just remember that the partition to be acted on must be unmounted.

Earl

---

### Post by supermooshman on 2010-10-09
> **deserthowler said:**
> You can change the label easily using gparted ... either through your desktop manager or with a live CD.  Just remember that the partition to be acted on must be unmounted.

Earl

many thanks, saved me from deleting and recreating the partition
(killing a mosquito with a bazooka... me?)

---

### Post by srs5694 on 2010-10-09
A couple more points:


[list]
[*]The tune2fs utility renames ext2/ext3/ext4 filesystems. If you want to rename another filesystem type, you'll need to use another tool, such as reiserfstune for ReiserFS or ntfslabel for NTFS.
[*]The "name" or "label" that's probably of interest here is in the *filesystem,* not the *partition.* This may seem like an obscure hair-splitting distinction, but it will soon become more important because of the impending rise of the GUID Partition Table (GPT). GPT, unlike MBR, supports *partition names.* The filesystem within a partition can have one name and the partition itself can have an entirely different name. I'm sure this will eventually cause problems, since different tools might display different names. GNU Parted and GPT fdisk, for instance, display the partition name; but GParted displays the filesystem name. Sooner or later somebody's going to become confused by this.
[/list]

---

