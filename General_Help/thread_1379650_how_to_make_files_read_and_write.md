---
title: "how to make files read and write"
date: 2010-01-12
forum: General Help
---

### Post by 26venger on 2010-01-12
i know that chmod +x makes a certain file executable but how do i make a file read and write. any help would be greatly appreciated.

---

### Post by bsussman on 2010-01-12
following your format, chmod +r and chmod +w are valid.

There are other formats - chmod xxx where xxx is a numeric code for the bit pattern to be applied is the one I like best.

man chmod to read how the numeric codes work ;)

---

### Post by Enigmapond on 2010-01-12
Depending on where the file is. In your home directory just right-click->properties->permissions and set them. If in the root, you need to browse as root or 
```
gksudo nautilus
``` 
and just do the same thing.

---

### Post by 26venger on 2010-01-12
thanks bsussman jus wat i was lookin fo

---

