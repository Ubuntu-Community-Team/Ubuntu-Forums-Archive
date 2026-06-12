---
title: "creating one PDF with multiple files"
date: 2006-02-24
forum: General Help
---

### Post by closeyourwindows on 2006-02-24
I have about 1500 html files I am attempting to put into one pdf document.  I have looked into html2pdf and I that seems to create a 1:1 file transfer.  does anyone know of any way to create this in to one pdf.  I thought I might be able to do $cat *.pdf but I am not sure of the turn out and sure there is a better way of doing this.  thanks.

---

### Post by simoncoul on 2006-02-24
Open office has a pdf export feature, if u can put all the files into an open office document then just export it and ur done.  I dunno if that will really help but that's how I make pdfs.

---

### Post by queenorych on 2006-02-24
libtiff-tools has a bunch of tiff/ps/pdf tools.  If you can make one ps you can us ps2pdf to convert it into a pdf.

---

### Post by closeyourwindows on 2006-02-24
I am not sure what you are refering too.  I went into synaptec and did not see anything like that.  I did a google search and there really is not too much out there unless you are willing to get the adobe suite for a cool G$.

---

### Post by ginapi on 2007-03-07
[LIST]
[*]Open you pictures with gThumb
[*]Select all pics you want to add to the PDF.
[*]File-print, set margins, zoom etc. as you like. 
[*]Click print.
[*]In the printer dialog select "Create a PDF document"
[*]If you dont like the default choose the file name and path clicking on 'Location'
[*]Click Print.
[/LIST]

This did the trick form me.

In this way you can also convert easily many pictures formats in pdf.

Bye  

ginapi

---

### Post by WW on 2007-03-07
The package **pdfjam** in the universe repository provides several commands for manipulating PDF files, include *pdfjoin*.  *pdfjoin* merges multiple PDF files into one file.

---

### Post by chewearn on 2007-03-07
I have a lot of success using pdftk.
_[http://www.accesspdf.com/pdftk](http://www.accesspdf.com/pdftk)_[]("http://www.pdfhacks.com/pdftk/")

You can find the pdftk package in universe repo.

---

### Post by moore.bryan on 2007-03-07
[I]closeyourwindows:
do i understand you right... you're looking to take a boat-load of html pages and convert them to ONE pdf file, without needing to convert EACH of the html pages to A SINGLE pdf file AND THEN merging those files into one?

good news, i've heard it can be done; bad news, no one has ever given me a way to do it.
[/I]

---

