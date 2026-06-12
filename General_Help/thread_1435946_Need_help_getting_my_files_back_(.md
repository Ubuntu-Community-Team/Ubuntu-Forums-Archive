---
title: "Need help getting my files back :("
date: 2010-03-22
forum: General Help
---

### Post by Strickenhaze on 2010-03-22
So here's my problem.

All my files are located on my /home ext4 partition. Windows has been installed so the windows boot loader doesn't know ubuntu's there (Please note I don't want to uninstall windows). I try to boot into an ubuntu 9.10 live disk, but it's unable to mount my ext4 partition. I try reinstalling grub, but it really doesn't seem to like working. I try reinstalling ubuntu to my old / ext4 partition (As to have grub installed and get everything working so I can copy things over), but whenever it starts to install it tells me that system files are already there and that it needs to format. It then takes me back to the partition manager, even if I delete the partition and made a new one, and even with "format" checked. Any ideas how I could get to my files so that I may copy them over to windows? Thanks!

Side notes: Ubuntu 64bit 9.10 was originally installed, and Windows 7 64bit is the working OS.

---

### Post by prodigy_ on 2010-03-22
> **Strickenhaze said:**
> I try to boot into an ubuntu 9.10 live disk, but it's unable to mount my ext4 partition.
Can you elaborate? Assuming that your ext4 partition is /dev/sda1, do the following commands work (from Live CD)?
```

sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt

```
If they give you errors, please post their output. Also post the output of ```
fdisk -l
```

---

### Post by Strickenhaze on 2010-03-22
It's sda4 haha.

```
sudo mount /dev/sda4 /mnt
``` just brings up the same error I've been getting: 

Unable to mount location

> mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



and as for ```
fdisk -l
```, just says 

>  
Disk /dev/sda4: 357.2 GB, 357215685120 bytes
255 heads, 63 sectors/track, 43429 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda4 doesn't contain a valid partition table



---

### Post by prodigy_ on 2010-03-22
Ok, let's try to debug this, starting with a simple: ```
sudo mount -t ext4 -o ro /dev/sda4 /mnt
```

Also, don't forget that for fdisk you need sudo too, so it's: ```
sudo fdisk -l
``` Fdisk output is important, because we need to check if /dev/sda4 is still a valid Linux (type 0x83) partition. I suspect that something is wrong and either fsck or testdisk will be needed.

---

### Post by Strickenhaze on 2010-03-22
This is what i get from everything...

> ubuntu@ubuntu:~$ sudo mount -t ext4 -o ro /dev/sda4 /mnt
mount: /dev/sda4 already mounted or /mnt busy
mount: according to mtab, /dev/sda4 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf39f1ab0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81920128+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           10200       10685     3903795    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3           10686       17372    53713327+  83  Linux
/dev/sda4           17373       60801   348843442+  83  Linux
Partition 4 does not end on cylinder boundary.
/dev/sda5           10200       10685     3903763+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 



Kind of scares me... it doesn't show up under computer like it used to... Just has "500 GB Hard Drive: 55 GB Filesystem, 500 GB Hard Drive:84 GB Filesystem" then all the normal Floppy Drive and Filesystem. I mean, still shows in fidisk from the looks of it. Just kind of freaky when you can't seem to get things to work right and you might lose everything haha.

---

### Post by prodigy_ on 2010-03-22
Well, your partition table looks normal ("does not end on cylinder boundary" is just a warning and may be safely ignored since partitions on your HDD don't overlap).

Have you used any kind of encryption software on your /home directory? If not, I suggest you to check /dev/sda4 with fsck to see if the filesystem is intact. Make sure that /dev/sda4 is NOT mounted! Then use this command: ```
sudo e2fsck -C /dev/sda4
```

---

### Post by Strickenhaze on 2010-03-23
Naa, I haven't encrypted it or anything. I tried what you gave me and got an output of this:

> ubuntu@ubuntu:~$ sudo e2fsck -C /dev/sda4

Invalid non-numeric argument to -C ("/dev/sda4")

ubuntu@ubuntu:~$ 


Thanks for all the help so far man.

---

### Post by prodigy_ on 2010-03-23
Sorry. Just omit -C (it's for logging purposes and not really needed). ```
sudo e2fsck /dev/sda4
```

---

### Post by Strickenhaze on 2010-03-23
Well, as of right now it's taking awhile. Just sort of sitting there.

This normal?

---

### Post by prodigy_ on 2010-03-23
> **Strickenhaze said:**
> Well, as of right now it's taking awhile. Just sort of sitting there.

This normal?
It should be checking the filesystem for errors now. If fsck didn't recognize the filesystem (if the first superblock were erased, for example) it'd just exit immediately. Generally, once it finishes and marks the filesystem as clean you should be able to mount this partition normally.

---

### Post by Strickenhaze on 2010-03-23
Any idea how long it'll take?

---

