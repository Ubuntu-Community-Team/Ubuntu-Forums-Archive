---
title: "Automatically download files from a TXT file"
date: 2009-10-08
forum: General Help
---

### Post by DouglasCaixeta on 2009-10-08
Hi,

I have an TXT file full of URLs to files. Each URL in a line. I want to download all of them. How can I do this automatically?

I'm wondering if it is possible to do it like the program plowdown. This program can download a files from RapidShare, Badongo and others, just typing plowdown file.txt, where file.txt contains all the URL, one per line. After it finishes one download goes automatically to the next. But it doesn't work with normal URLs.

Thanks in advance.

---

### Post by CatKiller on 2009-10-08
From **man wget**:

>              **-i** _file_
       **       --input-file=**_file_
                      Read URLs from _file_.

---

### Post by uylug on 2009-10-08
> **CatKiller said:**
> From **man wget**:

That's awesome. :D

---

