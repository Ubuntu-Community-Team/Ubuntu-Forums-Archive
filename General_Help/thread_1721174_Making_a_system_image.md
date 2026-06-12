---
title: "Making a system image?"
date: 2011-04-04
forum: General Help
---

### Post by listerdl on 2011-04-04
Hi is it possible to make a system image with ease?

By that I mean without having to fire up clonezilla and click through 15 clicks?

I am probably being lazy and have noticed the really easy way to make a system image in windows - is there something similiar in ubuntu?

Thanks

---

### Post by bluefrog on 2011-04-04
partimage
dd

---

### Post by seawolf167 on 2011-04-05
Yea, see the previous poster - personally, I like to make a Clonezilla image every couple months or so, then use rsync to keep the rest of my files current (daily) so if I have to restore I can just restore the old image, then copy over the file differences.

---

### Post by Mark Phelps on 2011-04-05
> **bluefrog said:**
> partimage
dd

Partimage does NOT work with Ext4 filesystems -- and this has been known ever since Ubuntu switched to using Ext4 filesystems as the default.

---

