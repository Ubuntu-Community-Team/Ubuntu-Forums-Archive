---
title: "Resize partition = No space left on device error"
date: 2009-11-12
forum: General Help
---

### Post by eimme on 2009-11-12
Hi all,

I decided to resize the partition on my storage drive (with gparted), all seemed to go well but now when I try to create directories or copy files to the drive I get a "No space left on device" error.

Also, even if I delete some files it does not allow me to replace them.

All of the files on the drive seem to be readable just fine and I can move the existing files into other directories with no problems.

There *is* space on the drive.
Checking the size of all the files reports:
175,840 items, totalling 839.8 GB

It is an ext3 partition.

One wierd thing is that Ubuntu (64bit karmic) still picks the drive up as "957GB Filesystem" in the Places menu.



Output of "df -h":
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             885G  842G     0 100% /media/acd61702-ff34-460f-8539-ac762d1dc466

```

Output of "df -i":
```

Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sdb1            58433536  175818 58257718    1% /media/acd61702-ff34-460f-8539-ac762d1dc466

```

I have ran "fsck -f -v /dev/sdb1":
```

fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  175818 inodes used (0.30%)
    8348 non-contiguous files (4.7%)
     142 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 76655/8046/56
222404925 blocks used (95.17%)
       0 bad blocks
      79 large files

  161176 regular files
   12907 directories
       0 character device files
       0 block device files
       0 fifos
      38 links
    1726 symbolic links (1512 fast symbolic links)
       0 sockets
--------
  175847 files

```

Any help would be appreciated.

Thanks,
e.

---

### Post by ajgreeny on 2009-11-12
Have you deleted large blocks of files as root, or more correctly, have you sent those files to root's trash?  It may be that you need to empty it if you have, and it should all be in /root/.local/share/Trash/files.  if that is not the problem I can't help any further, I'm afraid.

---

### Post by eimme on 2009-11-12
No, no large blocks of files have been deleted (and I also have no /root/.local), it was working fine before the partition resize and immediately after the resize this problem occured.

Note that the affected drive is not my main boot drive but simply a storage drive that I mount from the Places menu when needed.

just for the sake of more info, mount reports:
```

/dev/sdb1 on /media/acd61702-ff34-460f-8539-ac762d1dc466 type ext3 (rw,nosuid,nodev,uhelper=devkit)

```

Any more ideas? :)

---

