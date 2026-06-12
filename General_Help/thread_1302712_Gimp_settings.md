---
title: "Gimp settings"
date: 2009-10-27
forum: General Help
---

### Post by ub9876 on 2009-10-27
how can I set up gimp to perform a 1-2 clik scale conversion to a photo that I open with Gimp.. to make it resize to 
30% of its original size ...without going thru all the regular steps and save as    etc.....  and have it rename itself with a suffix to the file name that ID s it as a scaled image...????

---

### Post by StuartN on 2009-10-27
You could install ImageMagick and use:

```
convert -resize 30% image.jpg image_small.jpg
```

---

### Post by Vaphell on 2009-10-27
well, there is no macro recording i know of, you would have to learn how to write scripts. Maybe in not so distant future macro recording will get implemented.

---

### Post by ub9876 on 2009-10-27
ImageMagic is not in the repos... I still dont get the process for tarz files  and downloading them into a specific
directory...???

---

### Post by StuartN on 2009-10-27
> **ub9876 said:**
> ImageMagic is not in the repos.

I can see ImageMagick in the repositories all the way up to version 6.5.1 in Ubuntu 9.10 ([http://packages.ubuntu.com/karmic/graphics/imagemagick](http://packages.ubuntu.com/karmic/graphics/imagemagick)).

Try searching by name in Synaptic.

---

### Post by Skerit on 2009-10-28
> **ub9876 said:**
> ImageMagic is not in the repos... I still dont get the process for tarz files  and downloading them into a specific
directory...???

As StuartN said, it's "imagemagicK", with a ck at the end.
Tar.gz files mostly contain the source code of a certain program. You'd have to compile and install it yourself.

```
sudo aptitude install imagemagick
```

should do the trick.

---

