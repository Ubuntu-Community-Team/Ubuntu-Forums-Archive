---
title: "PDF printing - margins are off, losing text on both sides"
date: 2009-09-04
forum: General Help
---

### Post by jimmy the saint on 2009-09-04
I have tried multiple programs in both Ubuntu and Debian.  For some reason, whenever I print out a PDF file using evince or OOffice, I lose about 1/4 of an inch of text on both sides.  It is driving me nuts.  Scaling the PDF doesn't work, as it is no longer centered.  Is there anything I can do?  This is going to be very important this semester, important enough for me to maybe have to do a windows install just for this.  The last one died a horrible death and took my battery with it, so I would really like to avoid that route.

Thanks

---

### Post by jimmy the saint on 2009-09-04
Another piece of info that is likely relevant.  I just tried to trick the system into thinking it was using smaller paper.  I set the custom paper size to 8x10.5 and the result was the same image, just smaller.  The text is still cut off, but now there is a large margin on the right side (the lob is in landscape mode).  It appears that the image is being sent to the printer with the text cropped. hmmm

---

### Post by HermanAB on 2009-09-04
Howdy, note that you can send a PDF file straight to the print system.  You don't need to use a special program to print it.

The general command is:
lpr -H hostname -P printername filename.ps

and a specific example to print to the default printer is:
lpr -H localhost whatever.pdf

---

### Post by XCan on 2009-09-04
Weird error. What do you mean exactly with losing text on both sides? Are they outside of the printer's coordinates or is it just as if the text was not there, i.e., a narrow column with only the middle parts? 

How does the print preview look like? Does adobe do the same thing? What happens if you print out a non-pdf document?

---

### Post by fluffman86 on 2009-09-04
I love evince...it's lightweight and works well most of the time.  But sometimes, pdf's use Adobe specific stuff. 

[http://get.adobe.com/reader/](http://get.adobe.com/reader/)

Download to your desktop, then open a terminal:
```
cd Desktop
sudo mv *.bin /opt
cd /opt
./*.bin
```

That should work.

---

### Post by StuartN on 2009-09-04
I remember having similar problems in the past, and discovering that there were two different sets of controls for scaling - one in the print dialogue under (for instance) Document Viewer and a separate set in the Job Options under Administration->Printing for each specific printer. Disabling the checkboxes in Job Options sorted out the problem for me.

---

### Post by jimmy the saint on 2009-09-04
I use openbox, no gnome. So I dont have the gnome print manager.  I would install it, but I cant seem to find it in the repos.  What is it called?  I don't have adobe installed, I really don't want to, but I will if I have to.  Ill give it a shot.  I would really like to figure out evince/xpdf though.

As far a a description, it is essentially that the margins left and right edges of the pdf image are not being sent to the printer.  imaging tearing the left and right (landscape) 1/4 inch of a page of text, then pasting it onto a full page.  That is what is happening to the pdf.

---

### Post by jimmy the saint on 2009-09-04
> 
The general command is:
lpr -H hostname -P printername filename.ps

and a specific example to print to the default printer is:
lpr -H localhost whatever.pdf

The printer is a network printer off my router.  It is called 8500.  The result of using 8500 as the name is "8500: unkown printer"

---

### Post by jimmy the saint on 2009-09-04
Interesting.  lp worked.  lpr could not recognize the printer. The margins are correct the text is all there.  This is very frustrating.  I am filing a bug.  evince should not be destroying the pdf when printing it.

---

### Post by rogeroren on 2009-10-06
Maybe it's the printer type, as in the wrong printer driver. I had that problem with a Canon LC 700 until I changed drivers.

---

### Post by cdaaawg on 2010-01-13
I also have a problem with printing of a particular pdf which uses a 3 panel pamphlet format. Using Ubuntu 8.04 with evince to print, the first line is cut off by about 1/2 of its width. The print preview looks good prior to printing. Changing print margin settings in evince has no effect on the output. Using lpr, a small portion of the first column is cut off. I have not had any problems with 'normal' pdf documents, i.e. those that are not in pamphlet format.

---

