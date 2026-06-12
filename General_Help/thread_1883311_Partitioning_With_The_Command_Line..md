---
title: "Partitioning With The Command Line."
date: 2011-11-18
forum: General Help
---

### Post by dniMretsaM on 2011-11-18
First a little background. I have an SD card with Puppy installed on it and I want to shrink the partition down. It's formatted as ext4 and the lupusave.2fs is 1GiB. The total amount of used space is like 1.18 GiB. So using KDE Partition Manager I attempted to shrink it but I got the following output:
```
resize2fs 1.41.14 (22-Dec-2010)
/sbin/resize2fs: New size smaller than minimum (313259)
```I know that I can shrink the file system by running resize2fs with the -f (force) option, but I can't figure out how to shrink the actual partition. Any help would be greatly appreciated.

---

### Post by dniMretsaM on 2011-11-21
Bump.

---

### Post by wolfen69 on 2011-11-21
Have you tried Gparted?

---

### Post by MG&amp;TL on 2011-11-21
Have a look at:

```
man fdisk
```

Although be VERY careful where you aim it. +1 for gparted.

---

### Post by dniMretsaM on 2011-11-21
> **wolfen69 said:**
> Have you tried Gparted?

No, but I'm pretty sure it's a backend (resize2fs) problem. I get the same error when I run the command directly (unless I use the -f option). Miscalculation of the minimum is a known bug in resize2fs. I'll give GParted a shot, though.

---

