---
title: "making booklets"
date: 2010-04-03
forum: General Help
---

### Post by blackdalek on 2010-04-03
I've seen lots of threads about this with complex solutions using things like PSUtils etc. but nothing simple and easy.

Is there an easy way to print to a document to a PDF file so that it is properly formatted to be printed as a booklet?

For example, a 12 page booklet made up of A4 folded in half to A5 -
1st page = 12 & 1
2nd page = 2 & 11
3rd page = 10 & 3
etc.
So that when it is printed double-sided it comes out as a booklet.

The site at the following link does what I want perfectly if I upload the booklet in single pages format, but it would be nice to have a simple way to do it offline in ubuntu [http://bookletcreator.com/](http://bookletcreator.com/)

Thanks for helping!

---

### Post by llamabr on 2010-04-03
LaTeX could do this easily with, as you note, PSUtils, and also, as you note, easily, and offline, with ubuntu:

[http://tinyurl.com/ycxnqlk](http://tinyurl.com/ycxnqlk)
[http://www.mail-archive.com/debian-user@lists.debian.org/msg270060.html](http://www.mail-archive.com/debian-user@lists.debian.org/msg270060.html)

---

### Post by ajgreeny on 2010-04-03
Scribus may also be able to do this. I have used it occasionally in the past, but never for that purpose, so I am not totally sure, but many DTP applications can do this easily.

A quick look at OpenOffice also suggests that it can do it if you set up the printing properly.  In OOo help look for "booklet" and it gives some great help.  Not quite as good as a real DTP application, but nevertheless pretty good for a word processor.

---

### Post by coilwinder on 2010-06-03
Unfortunately, I don't know about any easy DTP solution either. I've just had a similar problem, and after some hours or trial and error I finally came up with a solution for an A6 (or, actually I'm a bit unsure about the exact size, maybe it's the "legal" size "equivalent"?) booklet. That is, 8 pages on one sheet of a double-sided A4 paper, using two-sided printing.

For a pdf file, you will need 4 utilities, for the 4 steps:

- pdftops  (pdf2ps will probably work too)
- psbook
- pstops
- ps2pdf

In my particular case, I had 12 pages that I padded to 16 before converting to postscript (.ps):
```
pdf2ps manual.pdf manual2.ps
```
Then I used "psbook" to rearrange pages for a 16-page booklet:
```
psbook -s16 manual2.ps manual3.ps
```
Then used pstops to merge 8 pages onto 2 sides (front and back side of a sheet of paper):
```
pstops '8:0@0.5(0,0.5h)+1@0.5(0.5w,0.5h)+4@0.5(0,0)+5@0.5(0.5w,0),2@0.5(0,0.5h)+3@0.5(0.5w,0.5h)+6@0.5(0,0)+7@0.5(0.5w,0)' manual3.ps manual4.ps
```
Afte this, one can convert back to a pdf:
```
ps2pdf manual4.ps manual5.pdf
```

However, my printer would not print this pdf (I cancelled after having waited 10-15 minutes a couple of times and also rebooting). Luckily, "document viewer 2.28.1" (default viewer for postscript files on my Ubuntu) could view and print the postscript file from the step before with no problem.

Afterwards, one would need to cut the A4 paper in half horizontally to create A5 size sheets. Then they need to be stacked on top of each other in the right order, and finally folded in half again to create an A6 size booklet.

Also, I cannot be certain that this solution works for more than 16 page booklets, but I don't see why not. I have just stumbled upon this method and have not tested it more than once.

For the moment I'm using Ubuntu 9.10 32 bit.

---

### Post by coilwinder on 2010-06-04
And, since I was on a roll (and, not least, I found an excellent explanation of how to make impositions with pstops here: [http://wiki.scribus.net/index.php/How_to_make_impositions_with_pstops]("http://wiki.scribus.net/index.php/How_to_make_impositions_with_pstops")) I also had to try to make an A5 booklet with 12 pages.

The main two differences from the above steps are:

1 - using psbook with -s12 parameter for a 12-page book:
```
psbook -s12 manual2.ps manual3.ps 
```

2 - And then the pstops settings for a two-sided printout:
```
pstops '4:0L@0.7(1w,0)+1L@0.7(1w,0.5h),2R@0.7(0,1h)+3R@0.7(0,0.5h)' manual3.ps manual4.ps
```

This time I could print out the pdf file after converting it, but the size was wrong (US letter), so I had to print out the last postscript file here as well. Oddly, this time "document viewer" could not show the contents on screen, but it printed fine.

Since I'm using A4 sheets to print on, I guess the "-pa4" argument should be used with pstops, but I did't see any difference without it (also, the pdf size was still wrong).


EDIT:

If I print the postscript file from the "print" button in the print preview window, from Document Viewer, the size is also wrong (US letter, but I wanted A4), but the preview seemed correct (or so I think it did, a bit unsure right now, sorry). However when printing directly from Document Viewer, it used the correct size. It would seem the thing to do is to close the preview window, and then bring up the print dialog again and print from that.

---

