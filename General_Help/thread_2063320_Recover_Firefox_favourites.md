---
title: "Recover Firefox favourites"
date: 2012-09-26
forum: General Help
---

### Post by Earl-Grey on 2012-09-26
Hello there,

I have Ubuntu saved on a hard drive but cannot boot anymore.

Is it possible to read the hard drive and get my favourites back in firefox by loading the wubi folder in win 7. I can view the Ubuntu folder, but not sure how to access the dir with the favourites.

If this is not possible could I load the hard drive on another ubuntu pc and retrieve the data?

---

### Post by pqwoerituytrueiwoq on 2012-09-26
if you have a way to browse the content of the wubi install yes
i have never used wubi
i think the file is places.sqlite in /home/user/.mozilla/firefox/{something}.default/
i have a bookmarkbackups folder in there that may be useful

---

### Post by bcbc on 2012-09-26
You can access a wubi root.disk with this tool: [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

Or you can mount a root.disk from a live CD.

---

### Post by Earl-Grey on 2012-09-27
Thank you very much, that work perfectly!!!!

---

