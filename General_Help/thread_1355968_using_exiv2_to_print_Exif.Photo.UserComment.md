---
title: "using exiv2 to print Exif.Photo.UserComment"
date: 2009-12-15
forum: General Help
---

### Post by Sycron on 2009-12-15
I tried using ```
exiv2 -Pt b.jpg
```but I get all the tags values> 26
hi_tom

```
exiv2 -Pnt b.jpg
```
> ExifTag                      26
UserComment                  hi_tom

How can I output just "hi_tom" ?

---

### Post by Sycron on 2009-12-16
I made it with ```
exiv2 b.jpg | awk '/Exif comment/ {print $4}'
```
Thanks!:popcorn:

---

