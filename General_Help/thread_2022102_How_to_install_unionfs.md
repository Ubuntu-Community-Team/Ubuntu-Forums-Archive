---
title: "How to install unionfs?"
date: 2012-07-10
forum: General Help
---

### Post by Paddy Landau on 2012-07-10
I would like to use [FONT=Lucida Console][unionfs]("http://manpages.ubuntu.com/manpages/hardy/en/man4/unionfs.4.html")[/FONT].

I know that I can install the program [FONT=Lucida Console][unionfs-fuse]("apt:unionfs-fuse")[/FONT], but I'd like to be able to use the mount command including from [FONT=Lucida Console]fstab[/FONT].

At the moment, trying to use [FONT=Lucida Console]unionfs[/FONT] from [FONT=Lucida Console]mount[/FONT] results in an error:
```
[COLOR=Navy]sudo mount --types unionfs --options dirs=~/test1:~/test2 unionfs /mnt/testu[/COLOR]
mount: unknown filesystem type 'unionfs'
```How do I install [FONT=Lucida Console]unionfs[/FONT] properly?

---

