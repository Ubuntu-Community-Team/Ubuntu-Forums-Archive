---
title: "Please recommend the best partition scheme for my setup"
date: 2011-02-22
forum: General Help
---

### Post by nkexplorer on 2011-02-22
I've done quite some research but haven't been able to figure out the best partition scheme for my use case. Please help.

- I have 4G ram, 1.5 TB x 2 internal hard drives.
- Ubuntu only for now. But down the road I "might" consider dual boot with Win7, or install some other linux distro to experiment.
- It'll be used as home multi-media center. Movie, music, document backups. I may also use it to host services such as http, ftp, etc..


Is below partition scheme secure and efficient?

Disk 1:
- swap  (2.5G)
- /boot (250M)
- /     (50G)
- /home (rest of the space)

Disk 2:
- swap  (2.5G)
- /home/drive2 (rest of the space)

---

### Post by Habitual on 2011-02-22
> **nkexplorer said:**
> Is below partition scheme secure and efficient?

Disk 1:
- swap  (2.5G)
- /boot (250M)
- /     (50G)
- /home (rest of the space)

Disk 2:
- swap  (2.5G)
- /home/drive2 (rest of the space)

You only need 1 swap partition.
The minimum partitions necessary for install are / /swap, and /home

Partition manually. Here are my recommendations assuming sda and sdb
sda:
15-20G for **/**
1G for **/swap** since you have enough RAM at 4G
**/home** can be the rest.

sdb:
format (if empty) sda**X** (**home2**) as any preferred filesystem you like
(I use ext4 on everything myself) and use all of it.
mount it at|as /home2 NOTE: If you can't mount it during the install, don't worry, it can be mounted after the install.
You may have to type in /home2 for the mount point.

Hope that helps.

---

### Post by nkexplorer on 2011-02-22
> **Habitual said:**
> You only need 1 swap partition.
The minimum partitions necessary for install are / /swap, and /home

Partition manually. Here are my recommendations assuming sda and sdb
sda:
15-20G for **/**
1G for **/swap** since you have enough RAM at 4G
**/home** can be the rest.

sdb:
format (if empty) sda**X** (**home2**) as any preferred filesystem you like
(I use ext4 on everything myself) and use all of it.
mount it at|as /home2 NOTE: If you can't mount it during the install, don't worry, it can be mounted after the install.
You may have to type in /home2 for the mount point.

Hope that helps.


Thanks Habitual. I planned to have 2 swap area on both drives to boost the performance a little when necessary.

Is 15-20G for "/" too limited? I try to make it enough space for future software installations in next 3-4 years. 50G sounds better?

1G swap sounded too small if I hibernate the system? I thought we have to leave at least 1 x ram size? Recommended 1.5 x ram size?

And yes I'll format all partitions as "ext4". Thanks for the advice on drive2. I'll mount entire disk 2 at "/home2".

---

### Post by seawolf167 on 2011-02-22
SWAP size = RAM size was when there was <1GB RAM on a normal computer, you can generally get away with 1/2 - 1/8 RAM size as SWAP nowadays unless you are doing something hugely memory intensive that will access the SWAP for storage (say rendering images).

10GB for / is now essentially required for a fresh install, 50GB may be a little much, but since you have 2x 1.5TB drives, its not like it will hurt you to allocate that much (you can always resize later anyways).

---

### Post by Habitual on 2011-02-22
nkexplorer:

I have a 2G /swap on my 4G RAM laptop and it never gets used.
But then again, I don't suspend or hibernate.

The only issue I can think where /swap may not be enough is if you have all 4G 'loaded up' and went to suspend or hibernate.

I have a 20G / and I am not afraid to install stuff.
```
20G  3.6G   16G  19% /
```

Others may have an opinion about this.

Worse comes to worse, you can always fire up gParted down the road and manipulate some free space from another partition over to the / partition should 20G prove not to be enough.
Or any partition that may need an 'adjusting' up or down.

Hope that helps.

---

### Post by srs5694 on 2011-02-22
Personally, I'd use LVM, at least for /home. That will give you one big partition for /home, without splitting it up artificially, the way you've suggested. Furthermore, if you use a few smallish LVM partitions, you can easily reassign one in the future for use by Windows. In sum, I'd do something like this:

/dev/sda:
- 20 GB Linux root (/) (primary)
- 20 GB LVM (primary)
- 100 GB LVM (primary)
- 1.3 (or whatever; the rest of the disk) GB LVM (logical)

/dev/sdb:
- ~200 GB LVM (primary)
- ~500 GB LVM (logical)
- ~800 GB LVM (logical)

Within the LVM, you'd then have:
- ~2 TB /home
- ~5 GB swap

If you like, you could also put the Linux root (/) filesystem in /home rather than in a regular partition. This is a bit easier if you've got a /boot partition outside of the LVM, although GRUB 2 is supposed to be able to read LVM data, so in theory this isn't necessary.

The use of five LVM partitions of varying size means that, should you want to install Windows in the future, you can shrink /home (if necessary), use pvmove to remove all the logical volume data from whatever partition(s) you want to use for Windows and for any shared-data partitions, use pvremove to remove the partition(s) from the LVM setup, and convert the partitions for use by Windows. If you're careful in the LVM setup, you can leave some free space that's allocated to the LVM but not actually used by the LVM, corresponding to whichever partition(s) you think you might use for Windows. This will greatly simplify a future Windows installation, while enabling you to quickly and easily expand /home should the need arise. Adjusting the LVM setup is likely to be less risky than the moving and resizing that would be necessary using a more conventional partitioning setup, although the biggest advantage remains as stated earlier: The ability to create a single logical volume for /home, which can be bigger than either of your 1.5 TB disks alone.

---

### Post by nkexplorer on 2011-02-22
> **srs5694 said:**
> Personally, I'd use LVM, at least for /home. That will give you one big partition for /home, without splitting it up artificially, the way you've suggested. Furthermore, if you use a few smallish LVM partitions, you can easily reassign one in the future for use by Windows. In sum, I'd do something like this:

/dev/sda:
- 20 GB Linux root (/) (primary)
- 20 GB LVM (primary)
- 100 GB LVM (primary)
- 1.3 (or whatever; the rest of the disk) GB LVM (logical)

/dev/sdb:
- ~200 GB LVM (primary)
- ~500 GB LVM (logical)
- ~800 GB LVM (logical)

Within the LVM, you'd then have:
- ~2 TB /home
- ~5 GB swap

If you like, you could also put the Linux root (/) filesystem in /home rather than in a regular partition. This is a bit easier if you've got a /boot partition outside of the LVM, although GRUB 2 is supposed to be able to read LVM data, so in theory this isn't necessary.

The use of five LVM partitions of varying size means that, should you want to install Windows in the future, you can shrink /home (if necessary), use pvmove to remove all the logical volume data from whatever partition(s) you want to use for Windows and for any shared-data partitions, use pvremove to remove the partition(s) from the LVM setup, and convert the partitions for use by Windows. If you're careful in the LVM setup, you can leave some free space that's allocated to the LVM but not actually used by the LVM, corresponding to whichever partition(s) you think you might use for Windows. This will greatly simplify a future Windows installation, while enabling you to quickly and easily expand /home should the need arise. Adjusting the LVM setup is likely to be less risky than the moving and resizing that would be necessary using a more conventional partitioning setup, although the biggest advantage remains as stated earlier: The ability to create a single logical volume for /home, which can be bigger than either of your 1.5 TB disks alone.

Thanks a lot! I'm fairly new to Linux in general. Heard of LVM but haven't been researching much on it yet. I'll read more and find out how it works. And again, absolutely valuable information. Much obliged!

---

