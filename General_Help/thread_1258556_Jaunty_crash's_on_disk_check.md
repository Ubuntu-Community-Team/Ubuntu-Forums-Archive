---
title: "Jaunty crash's on disk check"
date: 2009-09-05
forum: General Help
---

### Post by numbness05 on 2009-09-05
Hi there guys. I was really loving Jaunty on my laptop but it appears that when ubuntu wants to do its 30 or so bootup checks the whole thing crashes and I can never get past around 16% of the check all I can do is switch off and try again but with the same result each time. I cant even skip the disk check.

Has any body else heard of this happening?

I'm really tempted to try upgrading from intrepid to Jaunty again but really dont want to have to keep reinstalling it every 30 boot ups.

Any advice would be much appreciated.

Many thanks

---

### Post by Liolikas on 2009-09-05
You can edit /etc/fstab 
More info:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
< 5th and 6th columns: Dump and fsck options >
You want no fsck at all.

---

