---
title: "Could any 1 tell me how to read and write into .doc file using c program ..?"
date: 2011-01-31
forum: General Help
---

### Post by romy.mathew on 2011-01-31
Hi 

I was wondering how could I open a .doc file in c language. I tried to open a .doc file and it seems to displaying ASCII characters.

---

### Post by TeoBigusGeekus on 2011-01-31
A .doc file isn't actually a text file; or better it's not just a text file.
It has additional info about formatting, paragraphs, text boxes, etc and it can contain pictures, external references, drawings and other peculiar things.
All of the above not in a nice and clear formatted way (xml for example) but in microsoft's proprietary format.
So, reading a .doc file with C without knowing the internal binary structure of it, is prone to produce gibberish, as the binary values read by your program are interpreted as ASCII characters. I won't even start about writing to a .doc file with C...

---

### Post by uRock on 2011-01-31
Use Openoffice.org or you can open it in the Chrome browser by logging into a hotmail account and using the office application offered there.

---

