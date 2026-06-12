---
title: "gz problem."
date: 2010-11-01
forum: General Help
---

### Post by Drenriza on 2010-11-01
Anyone who can try and download the file from
[http://ubuntuforums.org/showthread.php?t=1545540](http://ubuntuforums.org/showthread.php?t=1545540) #7 (it's my own file) 

and extract it. I have tried myself but it says it's not a gzip format. Which i don't understand. I must be missing something.

So if anyone has luck extracting it, can you reply how you did.

Embarrassing problem. But hope for understanding :D that sometimes you make a f up. And just have a bad day where you cant think straight.

Thanks on advance.
Kind Regards.

---

### Post by gandaran on 2010-11-01
I was able to extract the package using [peazip]("http://peazip.sourceforge.net/") but dunno why it doesn't work with archive manager!

---

### Post by pholden on 2010-11-01
```
$ tar xf Ubuntu\ CLI\ PDF.\ V0.3\ 4-7-10.gz
```
That will extract the document from the tar archive :)

---

### Post by Drenriza on 2010-11-01
what on earth is going on.

I extracted it with peazip but its just a bunch of xml files. Where is the open office file :confused:

---

### Post by Drenriza on 2010-11-01
> **pholden said:**
> ```
$ tar xf Ubuntu\ CLI\ PDF.\ V0.3\ 4-7-10.gz
```That will extract the document from the tar archive :)

Ty but its strange because i already tried extracting it. Thus i also used an -z option. Maybe that screwed it up.

---

### Post by peculiar penguin on 2010-11-01
> **Drenriza said:**
> what on earth is going on.

I extracted it with peazip but its just a bunch of xml files. Where is the pdf :confused:
There is no PDF, you saved it as an Office Open XML file (which consists of a bunch of XML stuff in a zip archive with a .docx filename extension).

---

### Post by gandaran on 2010-11-01
> **Drenriza said:**
> what on earth is going on.

I extracted it with peazip but its just a bunch of xml files. Where is the pdf :confused:
what pdf? I don't see any .pdf file there!
why did you name it CLI PDF. should it be CLI .PDF?

---

### Post by Drenriza on 2010-11-01
Sorry my bad. I saw it was open office files, but with the power of my mind i was convinced that it was a pdf file :p corrected it.

And thus did not understand all the xml files at all.

---

