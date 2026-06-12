---
title: "I have ntfsprogs, but it doesn't seem to have ntfsck"
date: 2011-05-10
forum: General Help
---

### Post by avatarmonkeykirby on 2011-05-10
Every time I try to run ntfsck it tells me the command isn't found. Is it no longer included in the ntfsprogs package?

Using Lucid 10.04, up to date.

---

### Post by coffeecat on 2011-05-10
I think you may be thinking of ntfsfix, which is part of ntfsprogs. However, it is not a comprehensive filesystem checking utility. From man ntfsfix:

```
DESCRIPTION
       ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.

       You may run ntfsfix on an NTFS volume if you think it  was  damaged  by
       Windows or some other way and it cannot be mounted.

```The package description for ntfsprogs says this about what's included:

> The Linux-NTFS project ([http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)) aims to bring full
support for the NTFS filesystem to the Linux operating system.

This is a set of tools targeted for people interested in working
with the NTFS support in the Linux kernel and using it.  The
following utilities are included:

ntfsfix - Fix common filesystem errors and force Windows to check NTFS.

mkntfs - Format a partition with an NTFS filesystem, optionally bootable.

ntfsinfo - Show some information about an NTFS partition or one of the
files or directories within it.

ntfslabel - Show, or set, an NTFS partition's volume label.

ntfsresize - Resize an NTFS partition without losing data.

ntfsundelete - Recover deleted files from an NTFS partition.

ntfscluster - Locate the owner of any given sector or cluster on an NTFS
partition.

ntfscat - Concatenate files and print them on the standard output
(without mounting the partition).

ntfsls - List directory contents on an NTFS filesystem (without
mounting).

ntfscp - Overwrite files on an NTFS partition.

ntfsclone - Efficiently clone an NTFS filesystem or a part of it.

ntfsmount - Mount an NTFS partition from user-space using libntfs and FUSE.

ntfsdecrypt - Decrypt NTFS-encrypted files (NOT INCLUDED).

ntfscmp - Compare two NTFS volumes and tell the differences.That's in Natty but I guess it would the same in the Lucid version.

---

### Post by RJ_F1 on 2011-11-05
No, ntfsck is supposed to exist, per wikipedia. [http://en.wikipedia.org/wiki/Ntfsprogs](http://en.wikipedia.org/wiki/Ntfsprogs)

It does state, however that development for ntfsck seems to be suspended. And I read somewhere that ntfsck is not included in all "distributions" of ntfsprogs. I am looking into it now, however

---

