---
title: "umask=111 doesn't work in fstab"
date: 2011-06-26
forum: General Help
---

### Post by Seregwethrin on 2011-06-26
Hi,

I'm mounting my ntfs partition with ntfs-3g. I wanted today to remove executable bit from ntfs files. I want them to open with double click but I think because they are executable they are not opening with default associated programs, like Text Editor for txt files.

umask=111 the option I need but if I use it the ntfs partition doesn't mounted. 011 doesn't work too.

If i use umask=022 it works and mounts with permission 755, but that's not what I want. But it works.

Why umask 111 doesn't work do you know? Am I missing a point here?

My current mounting line for ntfs in fstab
```
/dev/sda5 /media/Dragon ntfs-3g defaults,uid=1000,gid=1000,locale=tr_TR.utf8 0 0
```

---

### Post by Seregwethrin on 2011-06-26
Okay I figured it out

Because of umask removes executable bit from directories too, it didn't mounted.

I used fmask instead of umask and everything is fine now :)

---

