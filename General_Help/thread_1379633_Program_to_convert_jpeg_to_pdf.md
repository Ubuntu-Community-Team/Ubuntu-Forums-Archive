---
title: "Program to convert jpeg to pdf"
date: 2010-01-12
forum: General Help
---

### Post by bhishan on 2010-01-12
Anyone knows a program to convert jpeg/jpg to pdf format?

---

### Post by miniyak on 2010-01-12
open office word processor

insert, image, from file, size to your liking

then export as pdf

---

### Post by kaibob on 2010-01-12
> **bhishan said:**
> Anyone knows a program to convert jpeg/jpg to pdf format?

The Imagemagick convert command-line utility.

```
convert file.jpg file.pdf
```

---

### Post by bhishan on 2010-01-13
Thanks!

---

### Post by glinsvad on 2010-03-03
> **kaibob said:**
> The Imagemagick convert command-line utility.

```
convert file.jpg file.pdf
```

For joining multiple images into one pdf, I've discovered that this just hangs:

```
convert page1.jpg page2.jpg file.pdf
```

whereas this works perfectly fine:

```
convert page1.jpg page2.jpg +compress file.pdf
```

---

### Post by Jesua on 2013-04-08
> **glinsvad said:**
> For joining multiple images into one pdf, I've discovered that this just hangs:

```
convert page1.jpg page2.jpg file.pdf
```

whereas this works perfectly fine:

```
convert page1.jpg page2.jpg +compress file.pdf
```

 Great.. it works wonderfull..

---

### Post by wildmanne39 on 2013-04-08
Old thread closed!

---

