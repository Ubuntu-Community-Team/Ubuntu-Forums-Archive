---
title: "How to remove execute from everything but folders?"
date: 2009-10-10
forum: General Help
---

### Post by CharlesA on 2009-10-10
Hi,

I made a "huge" screw up, in that when I setup my samba shares, the default permissions was 775, meaning everything has execute set.

Is there a way to remove that permission from all files, but leave the folders alone?

I want to do it from terminal if possible, since I've got a bunch of folders and it's a pain in the butt to open them all up in the GUI and remove the "execute" permission there.

sudo chmod 660 sets everything to rw, including the folders. I tried -x, but that did the same thing.

Any help is appreciated. :-)

---

### Post by yabbadabbadont on 2009-10-11
```
find /path/to/top/folder/that/is/borked -type f -exec chmod a-x {} +
```
If you need to change the directories instead of the files, then use "-type d".  The "find" man page has lots of information that can be useful in situations such as yours.  :)

---

### Post by CharlesA on 2009-10-11
> **yabbadabbadont said:**
> ```
find /path/to/top/folder/that/is/borked -type f -exec chmod a-x {} +
```If you need to change the directories instead of the files, then use "-type d".  The "find" man page has lots of information that can be useful in situations such as yours.  :)

Thanks! That seems to have done the trick!

---

