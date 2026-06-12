---
title: "Open source Adobe Acrobat alternative"
date: 2006-05-26
forum: General Help
---

### Post by michaeljb2005 on 2006-05-26
I'm looking for an opensource (free) alternative to adobe acrobat software.  Not the reader part but the editing part.  It should allow for extraction of pages, importation of pages and rotation of individual pages (not all pages at once like adobe reader) at a minimum.  Anyone have any ideas

---

### Post by KingBahamut on 2006-05-26
taking a stab here, you could try to install ps2pdf and create pdfs that way. ps2pdf just converts postscripts to pdf format. 

Additionally, Im assuming you could use Ghostscript ala GSview and Ghostview to create the nessecary postscript files, and then convert them to pdf format. 

Anyone else?

---

### Post by michaeljb2005 on 2006-05-26
[QUOTE=KingBahamut]taking a stab here, you could try to install ps2pdf and create pdfs that way. ps2pdf just converts postscripts to pdf format. 

Additionally, Im assuming you could use Ghostscript ala GSview and Ghostview to create the nessecary postscript files, and then convert them to pdf format. 

Anyone else?[/QUOTE]

Thanks for the suggestion but the problem isn't creating pdf files from word files or other document types, it's that I want to be able to manipulate/edit existing pdf files.

---

### Post by mostwanted on 2006-05-26
I believe KOffice has support for that (to some degree at least in version 1.5).

---

### Post by adamkane on 2006-05-26
There's almost nothing available to edit existing PDFs. You can create PDFs with OpenOffice (save as PDF) or with Kile (LaTeX2PDF).

---

### Post by BoyOfDestiny on 2006-05-26
[QUOTE=michaeljb2005]I'm looking for an opensource (free) alternative to adobe acrobat software.  Not the reader part but the editing part.  It should allow for extraction of pages, importation of pages and rotation of individual pages (not all pages at once like adobe reader) at a minimum.  Anyone have any ideas[/QUOTE]

Well, there is pdftohtml (it's in the repos). 

[http://pdftohtml.sourceforge.net/](http://pdftohtml.sourceforge.net/)

You can extract the text and images... Then I guess do whatever you want with it... Save it as a pdf from open office, or just print it to a postcript file, and convert that to a pdf...

EDIT: Also, looking in synaptic, pdftk seems useful too...
[http://www.accesspdf.com/pdftk](http://www.accesspdf.com/pdftk)

Sigh, I love having a centralized package manager... :)

---

### Post by ssam on 2006-05-26
you might want to look at Scribus, but i dont think it can import pdfs.

---

### Post by an.echte.trilingue on 2006-05-26
Scribus won't import PDFs, but I find that it is the best thing out there to to create them...

---

### Post by MartinJ on 2006-05-26
KWord, part of KOffice, will open pdf files.  You may have to fix some formatting after opening them though.

---

### Post by Jucato on 2006-05-26
While we're in the topic, I'd like to ask some questions:

1. Can pdftk convert PDF to HTML?
2. Does pdftk or pdftohtml have a GUI front-end?
3. Does anyone know how I can export PDFs to HTML in KOffice?

Thanks for the info! ;D

---

### Post by michaeljb2005 on 2006-06-11
[QUOTE=Fenyx]While we're in the topic, I'd like to ask some questions:

1. Can pdftk convert PDF to HTML?
2. Does pdftk or pdftohtml have a GUI front-end?
3. Does anyone know how I can export PDFs to HTML in KOffice?

Thanks for the info! ;D[/QUOTE]

I don't know the answers to the others but pdftk has a gui front end called GUIPDFTK here [http://www.paehl.de/pdf/?GUI_for_PDFTK](http://www.paehl.de/pdf/?GUI_for_PDFTK).  Have fun and thanks for all your input.

---

### Post by drdrgivemethenews on 2006-06-12
The bad news is I dont think there is a gui app to do what Adobe Acrobat does under linux eg make binders, delete single pages and import pages....I ma sure there are some command line one but they are hard to use after you have used Adobe GUI. 

The good news is that Linux in general has taken a big swing, so I read in a mag this month, to make pdf a standard in document management...this must mean that someone is going to come out with a manipulation package...doent it?

---

### Post by silvagroup on 2006-06-18
Had the very same problems. Needed Acrobat Pro so it was dual boot until I found win4lin. Now I can run both my windows apps in windows under Ubuntu. I spend the majority of my time in Ubuntu and 5-10 percent in win4lin/windows. One of these days win4lin will hopefully also go, but some one has to port Acrobat Pro and Libronix over to GNU/Linux.

---

### Post by Dominus Suus on 2006-09-15
Hullo michaeljb2005,
I've asked this question many times, too, and received the same 'use OpenOffice.org' response.  After some messing about, I discovered that you can get some of Acrobat Pro functionality doing the following:

1. Install cups-pdf from apt-get, which will be your Ad*be PDFPrinter.
2. Fetch PDFSaM (which is short for PDF Split-and-Merge) at [http://pdfsam.sourceforge.net/](http://pdfsam.sourceforge.net/) (no installation required).  I've found this an invaluable program for adding, inserting, and deleting pages from PDF documents - and that's about 60% of what Acrobat is good for.

Those two packages are sufficient for all of my PDF needs.  I haven't found anything for newer features like multimedia or encryption, but I'll keep pecking about.

---

### Post by brickbat on 2007-01-23
Here is what I just found...There is a program called Easy PDF that apparently runs perfectly under Wine.  It is neither free nor linux BUT it is GUI and it works.

[http://frankscorner.org/index.php?p=easypdf](http://frankscorner.org/index.php?p=easypdf)


[http://www.visagesoft.com/products/easypdf/](http://www.visagesoft.com/products/easypdf/)

---

### Post by Kumera on 2007-11-18
How can I install GUIPDFTK in Ubuntu?

---

### Post by silvagroup on 2007-11-19
> How can I install GUIPDFTK in Ubuntu?
Have you tried it in Wine. Here is a link that maybe of help. [http://www.paehl.de/pdf/?GUI_for_PDFTK]("http://www.paehl.de/pdf/?GUI_for_PDFTK")
I haven't it so I can't say for sure. I just run Pro in an emulator. Hope this helps.

---

### Post by Kumera on 2007-11-20
Yes, that works, thanks, although it does seem a little odd to be using Wine to run the Windows version of software that was originally written for Linux  :-)

---

### Post by beniwtv on 2007-11-20
Hi,

Perhaps PDFEdit suits your needs: [http://pdfedit.petricek.net/pdfedit.index_e](http://pdfedit.petricek.net/pdfedit.index_e)

They say there's even a .deb package.

---

### Post by K.Mandla on 2007-11-20
Moved to General Help. ;)

---

### Post by venik212 on 2008-01-04
I found a really simple solution to extracting pages from a pdf document:
1) Install a pdf printer driver (under cups)
2) Using the pdf printer, print to a file the range pf pages youi wish to extract.
3) In your home directory there will be a folder named PDF with the pdf files you created from the extracted pages.  

It works like a charm.

---

### Post by Payteer on 2008-01-09
How do you install a pdf printer driver?

---

### Post by brickbat on 2008-01-09
In Gutsy, I'm pretty sure its automatically installed.  In case it isnt, you can create it manually by installing cups-pdf through synaptic and then creating a pdf printer through the add printer dialog.  I had to do it manually in hoary and it was pretty easy but I can't remember the exact details.

---

