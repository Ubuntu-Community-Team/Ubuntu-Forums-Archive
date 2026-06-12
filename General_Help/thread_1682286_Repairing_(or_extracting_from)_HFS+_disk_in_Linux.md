---
title: "Repairing (or extracting from) HFS+ disk in Linux"
date: 2011-02-05
forum: General Help
---

### Post by IceCap on 2011-02-05
A friend of mine had an old iMac in which the harddrive developed some issues and I offered to help getting his photos from it.  When I hook it up to my Mac the hard drive shows up in Disk Utility but it can't mount it nor fix it.  I don't have Diskwarrior (or similar programs) so I was wondering if I could fix it from my Linux boxes (xubuntu).
  So my question is, is there a program in Linux that could extract the data from the drive or (even better) fix it?

  Thanks

  IC

---

### Post by srs5694 on 2011-02-05
As a general rule, it's best to use OS-specific tools to fix OS-specific filesystems, and both HFS and HFS+ are no exception to this rule. There is a Linux fsck.hfsplus utility (part of the hfsprogs package), and a symbolic link to this from fsck.hfs, but it looks like it's a port of fsck_hfs, which is OS X's tool for fixing HFS and HFS+, so fsck.hfsplus is unlikely to do any better than its OS X counterpart. I suppose it's worth trying, but I wouldn't pin too many hopes on it. It's also conceivable that Linux will let you mount the partition when OS X doesn't. I believe there are also non-mounting HFS and/or HFS+ tools, but I don't recall the details.

Failing that, you could try [PhotoRec,](http://www.cgsecurity.org/wiki/PhotoRec) which scans a hard disk for the "signatures" of know file types. In theory, this can recover lost files from just about any filesystem type. In practice, you may end up wasting a lot of time wading through files until you find the ones you want to recover.

---

