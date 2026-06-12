---
title: "dd from small to large drive results in bad superblock"
date: 2011-02-09
forum: General Help
---

### Post by lucasl on 2011-02-09
Hi,
I'm trying to 'upgrade' my 500gb drive to a bigger 1tb. I thought it would be as easy as using dd from the smaller to the larger then swapping them.

However, after using dd, although the partitions seem to be there on the 1tb drive, they all have a bad superblock and can't be mounted.

Is there any solution to this?

Thanks!

---

### Post by asmoore82 on 2011-02-10
`dd` should do the trick. But you could also try Clonezilla: [http://clonezilla.org/](http://clonezilla.org/)

---

