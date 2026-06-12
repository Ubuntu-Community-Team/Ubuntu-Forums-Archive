---
title: "Wildcard * not finding results"
date: 2011-12-28
forum: General Help
---

### Post by crutch145 on 2011-12-28
When searching directories using a wildcard *.jpg or *.txt, etc. it finds 0 items.  I have verified that the directory I am searching in does in fact have files with the .jpg and .txt extension.  Any ideas?

Thanks,

Justin

---

### Post by guestolo on 2011-12-28
try removing the wildcard
as eg..
.jpg

---

### Post by crutch145 on 2011-12-28
That does work for the example of .jpg.  But if I try to search with all .jpg files that begin with IMG, e.g. IMG*.jpg it does not find anything.  Basically the wildcard * is broken... and I have no idea why :-/

---

### Post by guestolo on 2011-12-28
I've never really thought much about it, but the following seems to work

If you were to search in terminal 
Search Documents folder asEg...
ls *.jpg

Result would show just the .jpg files in Documents folder
.jpg in Search box results all .jpg files in Documents folder and it's subfolders

In your eg. of searching for Img*.jpg

Try running that in the search field without the wildcard, but use a space
As eg..
Use>>> Img .jpg
don't use>> Img.jpg

---

### Post by crutch145 on 2011-12-28
Wow, that is awesome.  A blank space in place of an * works like magic.  Thanks!

---

