---
title: "List images with their dimension"
date: 2010-02-20
forum: General Help
---

### Post by sombrancelha on 2010-02-20
Hello,

I want to list the images in a directory with their dimensions, if possible in order of their widths (all the wider pictures come first) - this is not strictly necessary, but would help me.

I read the ls manpage, but couldn't find anything related to it.

Thanks.

---

### Post by RedSingularity on 2010-02-20
What about listing files by their size?  I know thats possible but i have never heard of listing files according to their pixel size.  I am not a graphics design major but i would assume that bigger pictures will have a larger file size.

---

### Post by Girya on 2010-02-20
> find -name *.jpg -exec identify -format '%w %h\n'  {} \;


this command will output the sizes of the jpg without the file name. I don't know how to list the file name with the size. but maybe you can figure that part out and post the solution

here is the link that discusses a similar challenge:

[http://ubuntuforums.org/showthread.php?t=1408744]("http://ubuntuforums.org/showthread.php?t=1408744")

---

### Post by Girya on 2010-02-20
```
find -name *.jpg -exec identify {} \;
```

okay this command does what you want

---

### Post by sombrancelha on 2010-02-20
> **RedSingularity said:**
> What about listing files by their size?  I know thats possible but i have never heard of listing files according to their pixel size.  I am not a graphics design major but i would assume that bigger pictures will have a larger file size.

I did try this, but the pictures were not completely divided.

I have six picture dimensions:
2560x1920 and 1920x2560
4000x2248 and 2248x4000
4000x3000 and 3000x4000

And I want them all to have width 2048 (for the first column) or height 2048 (second column).

If I just use
```

mogrify -resize 2048 *

```

I'd get all of them with **width** 2048.

So I thought I'd separate all images according to their dimensions, and then just resize them by groups.

Alternatively, if someone knows, I could use a mogrify command that would recognize if it should make height 2048 or width 2048.

EDIT: Thanks Girya, your command worked

---

### Post by Girya on 2010-02-20
I'm sorry I thought you wanted to list the photos by size.

you can pipe the output of the command i gave you into a file then sort them by by size using grep

---

