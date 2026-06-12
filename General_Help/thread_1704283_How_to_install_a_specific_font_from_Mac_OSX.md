---
title: "How to install a specific font from Mac OSX?"
date: 2011-03-10
forum: General Help
---

### Post by mexp on 2011-03-10
I received from a designer a zipped folder called "__MACOSX", and there are two font files, "._BCongress.scr" and "._BConNor".

How do I get these fonts installed? 

I could not find any instructions on how to do this - I found the font converter Fondu, but it didn't seem to understand these file formats. I can't open them in Ubuntu Font Viewer either.

---

### Post by coffeecat on 2011-03-10
Are you sure those are font files? MacOS uses a leading dot to hide files just like Linux so those two files would be hidden ones in MacOS, which would be an odd thing to do with a font file. And anyway, a file preceded by ._ when created in MacOS is often the redundant resource fork. See here:

[http://support.apple.com/kb/TA20578](http://support.apple.com/kb/TA20578)

I wonder if your designer has made an error in preparing the zip. I also wonder if those two files are the resource forks of files that are not the actual font files. How large are they?

---

### Post by mexp on 2011-03-10
Yea, you may be right. The files are 9.1 KB and 33.4 KB - so they seem pretty small to be real font files. I was almost sure that I had installed these fonts before from this same archive :-/

---

### Post by mexp on 2011-05-03
Actually, the resolution for this was to use utility called t1unmac. 

I converted the mysterious ._BConNor.pfa and ._BConNor.afm files, and one of them (don't remember any more which one it was) became Ubuntu-readable and istallable font file...

---

