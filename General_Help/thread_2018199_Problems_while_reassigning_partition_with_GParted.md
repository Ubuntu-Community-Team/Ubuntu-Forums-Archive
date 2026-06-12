---
title: "Problems while reassigning partition with GParted"
date: 2012-07-06
forum: General Help
---

### Post by Macamba on 2012-07-06
Hi,

I have a NTFS partition I would like to use for my Ubuntu system. The NTFS partition is freed from data so it's ready to go. 

When I start GParted I see a triangle containing an exclamation mark in it. When I request Information I get:
```
Unable to find mount point
Unable to read  the contents of the filesystem!
Because of this some operations may not be available.

The following list of software packages is required for ntfs
file system support: ntfsprogs.

```

This is a rather big partition I once found back. I made it NTFS.

What I would like to do is make it EXT3 and mount it automatically when I start Ubuntu. I should use GParted for that. So what do I need to do?

TIA,
Macamba

---

### Post by Macamba on 2012-07-06
I found it (*SIGH*). The partition was not properly unmounted. :rolleyes:

---

