---
title: "Question on how to use the pdf2djvu command"
date: 2011-02-24
forum: General Help
---

### Post by RonB123123 on 2011-02-24
Hi. 

I'm trying to convert the first 100 pages of a PDF to a DJVU file because DJVU files are very quick to open. Anyway, my current command is:

pdf2djvu -o surveying.djvu 013*.pdf -pages=1-100

and the output I get is: Unable to parse page numbers

What am I doing wrong?

FYI [http://code.google.com/p/pdf2djvu/wiki/ManualPage](http://code.google.com/p/pdf2djvu/wiki/ManualPage)

~Ron

---

### Post by RonB123123 on 2011-02-26
> **RonB123123 said:**
> Hi. 

I'm trying to convert the first 100 pages of a PDF to a DJVU file because DJVU files are very quick to open. Anyway, my current command is:

pdf2djvu -o surveying.djvu 013*.pdf -pages=1-100

and the output I get is: Unable to parse page numbers

What am I doing wrong?

FYI [http://code.google.com/p/pdf2djvu/wiki/ManualPage](http://code.google.com/p/pdf2djvu/wiki/ManualPage)


This command works to convert every page but fails before creating the djvu:
pdf2djvu -o surveying.djvu 013*.pdf 

but after it completes all 900 pages, it fails because of some bookmarking issue at the very end. If I change the command to:
pdf2djvu -o surveying.djvu 013*.pdf -pages=1

it will work perfectly but I don't want to run a separate command for each page, or run a bash script that will run it 900 times because it will create 900 djvu files when I only want one. Apparently, one file is possible, but I need to figure out how to setup converting page ranges. 

Has anyone figured this out?

If you're curious why I'm trying to convert a 140 MB PDF to a 40 or 50 MB DJVU, it's because a DJVU file is faster to open and faster to load individual pages. Whereas a PDF, will have a 1 or 2 second delay. 

Ron

---

### Post by RonB123123 on 2011-02-26
Oops. I just realized my mistake. I meant to use **--pages** instead of -pages. Now it works fine. :D

---

