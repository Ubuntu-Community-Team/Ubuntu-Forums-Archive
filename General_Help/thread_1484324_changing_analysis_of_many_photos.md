---
title: "changing analysis of many photos"
date: 2010-05-15
forum: General Help
---

### Post by geo909 on 2010-05-15
Hello all,

I've been taking pictures with my camera using the best quality,
so that every picture was more than 8 MB's. After a couple of 
years I ended up with a huge folder of many GB's. Is there a
command line tool that could lower the quality (and therefore
the size) of the pictures? I would like to use some script to
do that recursively in all my folders with photos..

Thanks a lot in advance..

---

### Post by StuartN on 2010-05-15
> **geo909 said:**
> Hello all,

I've been taking pictures with my camera using the best quality,
so that every picture was more than 8 MB's. After a couple of 
years I ended up with a huge folder of many GB's. Is there a
command line tool that could lower the quality (and therefore
the size) of the pictures? I would like to use some script to
do that recursively in all my folders with photos..

Thanks a lot in advance..

Imagemagick's **convert** command will work.

Use **find . -iname "*.jpg"** to call convert for every file in a folder hierarchy.

---

### Post by geo909 on 2010-05-16
> **StuartN said:**
> Imagemagick's **convert** command will work.

Use **find . -iname "*.jpg"** to call convert for every file in a folder hierarchy.

Thanks so much! That's exactly what I was looking for..

---

