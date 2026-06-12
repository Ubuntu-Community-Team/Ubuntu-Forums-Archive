---
title: "Extracting jpg info"
date: 2011-10-23
forum: General Help
---

### Post by Ron W on 2011-10-23
I am wanting to extract the image width and height information from a jpg file, so that I can get a programme to determine whether an image is vertical or horizontal.

Though 'exiftags' can extract this information it does NOT change the dimensions around when the image has been rotated by 90 degrees using 'Eye of GNOME' the 'The GNOME image viewer'.

However, on right-clicking the image's thumbnail, choosing 'Properties', and then choosing the 'Image' tab, then the width and height are correctly given. How can I get this information?

Thanks

Ron

---

### Post by TeoBigusGeekus on 2011-10-23
If you have imagemagick installed, try from terminal with the identify command
```
identify /path/name.ext
```

---

### Post by WasMeHere on 2011-10-23
+1 for ImageMagick

There are very good tutorials on the internet, so have fun learning about it :-)

Olle

---

### Post by Ron W on 2011-10-23
Thanks for your suggestion, TeoBigusGeekus. I've got the information that I was looking for.

Ron

---

