---
title: "compressing .jpeg files"
date: 2011-02-23
forum: General Help
---

### Post by nischalinn on 2011-02-23
I want a huge file of .jpeg files. How can I can compress these files to save my space? Is there any s/w for this??

---

### Post by rubylaser on 2011-02-23
jpegs are a lossey format, and as result are already compressed.  You could make a tar bz2, xz, or lzma to compress them more.  Another idea would be to use mogrify from Imagemagick to scale the images down, or slightly reduce the quality if you want to get back more space.

---

### Post by epud on 2011-02-23
To compress the files you can right click on the folder containing the files the choose Compress..

You will then see all the options for compressing your files. tar.bz2 compresses the files more than tar.gz but also uses more resources in doing so.

---

