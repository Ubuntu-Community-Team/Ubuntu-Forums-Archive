---
title: "printing pdfs without images"
date: 2009-10-26
forum: General Help
---

### Post by sa-mejia on 2009-10-26
My wife is taking an art history course, and has had to print a good deal of articles in PDF format.  These include a good number of  images, which  are useless when printed out (we have a black and white printer), but do waste a lot of ink from the printer. 

Anyone has any idea if there are any solutions to this?  Is there any way to print the pdf text only without printing the images (or with blank images that waste no printer ink)?  

Thanks in advance.

Santiago Mejia.

---

### Post by sa-mejia on 2010-02-19
bump?

---

### Post by orky7 on 2010-02-19
i don't know any such application but what i do is that copy the content to gedit or openoffice word and this editors keep the indentation of the copied text so this trick just work for me.

---

### Post by niteshifter on 2010-02-19
Hi,

Depending upon how the pdf's were made the command line tool pdftotext might be useful. It's part of poppler-utils:
```
sudo apt-get install poppler-utils
```
```
pdftotext -layout -eol unix somefile.pdf somefile.txt
```
The above will take in somefile.pdf and produce somefile.txt, containing only the text, preserving the layout and unix-style line endings. You could then take that .txt file, clean up the formatting if need be in OOo Writer, Abiword (or whatever word processor you favor) and print it.

Caveat: Not all PDF's will work with this. Some scanner-software produced PDFs may fail - they don't have any text, just an image of the text.

---

