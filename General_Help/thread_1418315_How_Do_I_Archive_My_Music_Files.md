---
title: "How Do I Archive My Music Files?"
date: 2010-02-28
forum: General Help
---

### Post by goatgonads on 2010-02-28
I have a ton of music that I would like to upload to an on-line storage site. Ideally, I would like to keep the file organization structure intact, but am limited to 50mb file size.

Is there a way to compress this whole directory without going through and compressing every folder individually, while maintaining less than a 50mb file size?

---

### Post by asmoore82 on 2010-02-28
you can create a multi-part archive with the help of the `split` utility...

```
tar cvz ~/Music | split -d -a 3 -b 48M - music-archive.tar.gz.
```

the same archive can be restored with `cat` ...

```
cat music-archive.tar.gz.* | tar xvz
```

---

### Post by goatgonads on 2010-02-28
That would work if I were to archive the whole directory as one file, I was hoping to have each sub folder (album) as its own archive of less than 50mb. This would allow me to add more albums later, or to just grab what I need.

---

