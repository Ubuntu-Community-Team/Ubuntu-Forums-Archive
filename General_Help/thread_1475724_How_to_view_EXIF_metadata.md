---
title: "How to view EXIF metadata"
date: 2010-05-07
forum: General Help
---

### Post by krige on 2010-05-07
Hello,

does anybody know how can I view JPG EXIF metadata in any of the following programs?

- GIMP;
- F-Spot;
- Eye of Gnome.

---

### Post by micheledm on 2010-05-07
In F-Spot there's a dropdown menu at the top of the left panel. In the default view should be selected the "Tag" view by default but there's also the "Metadata" views

---

### Post by krige on 2010-05-07
Thank you micheledm! :)

I still wonder how to do it with the other two programs.

---

### Post by dino99 on 2010-05-07
you may have libexif12 installed

---

### Post by StuartN on 2010-05-07
> **krige said:**
> does anybody know how can I view JPG EXIF metadata in any of the following programs?

I don't think Gimp shows EXIF data, although it does preserve it in modified files. You can install a plugin like [http://registry.gimp.org/node/8839](http://registry.gimp.org/node/8839)

gThumb has very good EXIF handling, with a popup dialog that follows image selections, so that you can compare EXIF data between images.

---

### Post by krige on 2010-05-07
> **dino99 said:**
> you may have libexif12 installed

Yes, I do :)

```
dpkg -l | grep exif
ii   libexif12   0.6.19-1   library to parse EXIF files
```

---

### Post by krige on 2010-05-07
> **StuartN said:**
> gThumb has very good EXIF handling, with a popup dialog that follows image selections, so that you can compare EXIF data between images.

Thank you StuartN, I will give it a try :)

---

### Post by krige on 2010-05-07
> **StuartN said:**
> gThumb has very good EXIF handling, with a popup dialog that follows image selections, so that you can compare EXIF data between images.

I have found gThumb features richer and more intuitive to use than F-Spot. More importantly, with gThumb I can import videos together with photos!

---

