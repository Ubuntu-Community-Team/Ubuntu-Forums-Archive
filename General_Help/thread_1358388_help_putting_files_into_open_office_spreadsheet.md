---
title: "help putting files into open office spreadsheet"
date: 2009-12-18
forum: General Help
---

### Post by lilithdog on 2009-12-18
Hi,

I am copying and pasting (by hand) a really large file into open office spreadsheet.  The trouble is I can't get the whole file to print so that I can copy the thing by hand.  It cuts off somewhere in the middle and I can't get the terminal to go up any further so I can select it for copying.  I am using the 'cat *file*' command to see the file.

I know this is a*** really*** basic question, but can someone help?

---

### Post by Darael on 2009-12-18
If you use "less" instead of "cat" you can scroll the entire document with the arrow keys or mouse wheel.

---

### Post by lilithdog on 2009-12-18
I see that I can view the whole file but how do select the whole thing for copying?

---

### Post by lilithdog on 2009-12-18
> **lilithdog said:**
> I see that I can view the whole file but how do select the whole thing for copying?  Actually, I still can't see the whole output file.  I can select it, but it still stops half-way through the file...

---

### Post by SlugSlug on 2009-12-18
due to the size then, would it not be better to use a gui

eg:
gedit [filename]

---

### Post by oldfred on 2009-12-18
Cannot you just import it with insert sheet from file. I regularly read in text files. Some work better than others depending on how the text is formatted.

---

### Post by gdonwallace on 2009-12-18
This can also depend on the version of open office and the number of lines in the file you are trying to open in OOo.  

Some older  versions of OOo only allow 36,000 lines in the spread sheet.  The one thing I have not figured out yet is that on some distros, the newest version of OOo will allow over 1 million lines and some wont.  If you are using the most recent OOo on Ubuntu, then you should have enough lines.  

I would first start by opening the file in gedit.  It would make the copy and past so much easier.  Open a open office spreadsheet.  In gedit, do a CTRL + A; this will select everything.  Then copy and paste into open office.  That should take care of it for you.  Trying to copy and paste from terminal to Spreadsheet is un-necessarily difficult when the same thing can be accomplished from within Gnome so much easier.

---

### Post by lilithdog on 2009-12-18
Thanks everybody!!

---

