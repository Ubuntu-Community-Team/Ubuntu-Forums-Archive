---
title: "pdf checker"
date: 2011-09-06
forum: General Help
---

### Post by DrPL on 2011-09-06
Hello,
I've written a document using OpenOffice and have converted it to
pdf format so that it can be printed as a book on Lulu.com ; however, they are unable to print it, citing a RIP error. The pdf looks fine at my end and I was wondering if there was a pdf checker that I could download to determine where the errors are?

Best wishes

Paul

---

### Post by JC Cheloven on 2011-09-06
Hi, [google is magic]("http://www.pdfa.org/doku.php?id=pdfa:en:products:validate").

From there, I just used a trial of "PDF-A manager" from a company named pdftron, to validate the compliance of some PDF-A files I generated with OpenOffice and LibreOffice. You can downoad it from [here]("http://www.pdftron.com/pdfamanager/downloads.html") if you decide to trust the executable (I don't endorse it in any way, do it at your own risk!). The tar.gz file comes with an standalone executable and all pertinent instructions.

Hope this, or any of the places in the first link above, helps you. 
If it does, please take a moment to share your experience (I'm interested as well).

Cheers
JC

---

### Post by DrPL on 2011-09-07
Yes I'd seen that but I didn't want to spend lots of money on something I may only use once.

It did produce an output file but I have no idea what the errors mean, how to locate them or how to correct them.

---

### Post by debd on 2011-09-07
try saving the document as a .doc file and then convert it with a command line utility named **wvPDF**. 
```
 wvPDF <source doc file name> <dest. file name>
```
or you can find some other way to generate the pdf file.
run ```
apropos pdf
``` to get a listing of hosts of cli programs to manipulate pdfs.

---

