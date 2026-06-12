---
title: "mogrify recursively?"
date: 2011-01-09
forum: General Help
---

### Post by sohlinux on 2011-01-09
How can I mogrify recursively resizing and compressing all images in all subdirectories?

the following code only works if I am inside a directory with images

```
mogrify -resize 3000 -compress JPEG -quality 85 *.jpg
```

---

