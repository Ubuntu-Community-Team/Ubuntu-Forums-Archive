---
title: "search hdd"
date: 2010-02-01
forum: General Help
---

### Post by brandon_h on 2010-02-01
How do I do a All Image Search in Karmic?

There are a few images on my hard drive, I KNOW they're there, I just can't find them....

---

### Post by M1GEO on 2010-02-01
If you know the extension (file type), you can do something like
```
find -iname "*.jpg"
```

That will find all JPG images in the directory, and further down the directory tree (in all subsequent directories).

You may also wanna check out *.png, *.gif, etc.  But jpg is most likely to be a camera image.

---

### Post by brandon_h on 2010-02-01
Thanks....

---

### Post by bluelamp999 on 2010-02-01
There's also Catfish It's in the repositories, here's some info - [http://www.addictivetips.com/ubuntu-linux-tips/catfish-file-searching-tool-for-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/catfish-file-searching-tool-for-ubuntu-linux/)

---

### Post by jamesisin on 2010-02-01
If appropriate please mark your thread as SOLVED in Thread Tools above.

---

