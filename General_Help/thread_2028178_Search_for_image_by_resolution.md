---
title: "Search for image by resolution"
date: 2012-07-17
forum: General Help
---

### Post by rhss6-2011 on 2012-07-17
Hey there,
I'm getting into shell/bash scripting, and I use my terminal for almost everything. Most of what I do runs off of scripts that I have, including a customized application menu using Zenity...

I was wondering if (using my terminal) there's a **terminal command** I can use, to **search for images with a specific resolution**.

Any help would be greatly appreciated, since this would help me work on a script I've been trying to bring to perfection...

---

### Post by sudodus on 2012-07-17
Try ***identify***. Install ***imagemagick*** if you don't have that program installed.

for some files in a directory:
```
[COLOR="RoyalBlue"]$ identify *.jpg[/COLOR]
img_4600.jpg JPEG 3264x2448 3264x2448+0+0 8-bit DirectClass 2.28MiB 0.000u 0:00.000
img_4601.jpg[1] JPEG 3264x2448 3264x2448+0+0 8-bit DirectClass 2.248MiB 0.000u 0:00.000
img_4600b0.jpg[2] JPEG 1200x1200 1200x1200+0+0 8-bit DirectClass 444KiB 0.000u 0:00.000
img_4600b1.jpg[3] JPEG 1200x1200 1200x1200+0+0 8-bit DirectClass 326KiB 0.000u 0:00.000
img_4600b3.jpg[4] JPEG 984x1248 984x1248+0+0 8-bit DirectClass 243KiB 0.000u 0:00.000
img_4600b4.jpg[5] JPEG 984x1248 984x1248+0+0 8-bit DirectClass 300KiB 0.000u 0:00.000

```
so you have the resolution in the 3rd column and can sort, cut, grep according to that.

For example:
```
identify *.jpg|sed s/\[[0-9]*\]// |cut -d\  -f1,3|grep 1200x1200$
``` will list the files with the resolution 1200x1200
```
img_4600b0.jpg 1200x1200
img_4600b1.jpg 1200x1200
```

---

### Post by rhss6-2011 on 2012-07-18
Thanks a lot, that helped quite a bit!

---

