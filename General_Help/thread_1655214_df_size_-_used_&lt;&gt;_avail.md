---
title: "df size - used &lt;&gt; avail"
date: 2010-12-29
forum: General Help
---

### Post by herta on 2010-12-29
My rsync backup crashed because of a disk full error.  I tried to free space by removing old files that I no longer need.  But although I meanwhile wiped some 8GB, df still claims that the disk is 100% in use.  What is weird is that when I remove files, I can see the Used counter go down, but unfortunately, there is no corresponding increase in the Avail counter:

# df -h /bck
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4             221G  213G     0 100% /bck

I ran lsof and fuser, unmounted and remounted the device, so I'm sure there are no processes that still have open files.

environment:
Ubuntu 10.10 (maverick) - Linux uhuru 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux

# mount | grep bck
/dev/sda4 on /bck type ext4 (rw,errors=remount-ro)

Any idea?

Kind regards,

Herta

---

### Post by hawkmage on 2010-12-29
What do you get from this command:
```
sudo dumpe2fs -h /dev/sda4 | grep -Ei 'block|inode'
```Specifically what is the value for the "Reserved block count" and "Free blocks".  It the reserved block count is greater than the Free blocks then only root will be able to crate files on that file system.

---

### Post by herta on 2010-12-29
Looks like you hit it in 1:

# dumpe2fs -h /dev/sda4 | grep -Ei 'block|inode'
dumpe2fs 1.41.12 (17-May-2010)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Inode count:              14655488
Block count:              58595079
Reserved block count:     2929753
Free blocks:              1623924
Free inodes:              14619546
First block:              0
Block size:               4096
Reserved GDT blocks:      1010
Blocks per group:         32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Journal inode:            8
Journal backup:           inode blocks

Thanks!

Herta

---

### Post by hawkmage on 2010-12-29
It was one of the things that stuck in my head after taking a Solaris Fault Analysis class.

If you want to find large files on that file system owned by root try the following:
```
sudo find / -mount \( -uid 0 -o -gid 0 \) -size +100M -ls
```This will find all file owned by root (UID 0) or in the root group (GID 0) that are larger than 100 MB.

---

