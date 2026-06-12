---
title: "Convert a PDF file page format"
date: 2010-01-20
forum: General Help
---

### Post by t09 on 2010-01-20
I have a PDF File here with upright ("portrait" format) pages, and I want to convert it so that each page gets "split" in the middle and becomes two wide ("landscape" format) pages. 

Something like "print multiple pages on one page", only reversed ;)

Is there any way to do such a thing with CUPS or something?

I have the source file ONLY in PDF Format, I'm afraid. :|

---

### Post by phillw on 2010-01-20
Hi, and welcome.

Ermmm... how many pages ?

You can manipulate a pdf page with GIMP, so you could load it into GIMP, highlight the area you want, and then copy and paste it into a new document created at the size you want.

There's another programme that can read a pdf file and extract out the graphics and text into seperate files so you can manipulate them how you want to build a new page.

Those are the only two things i can think of - others may have additional ideas

Regards,

Phill.

---

### Post by t09 on 2010-01-20
It's a 93 Page eBook... 

editing with GIMP is not too optimal, first it can't export the edited PDF and second: I want the Pages to be splitted and I need the top and bottom half of each page ... with GIMP I could only crop the Image to a selected area.

:|

might it be possible to simulate printing in 200% size, where each page is being rotated 90° and separated onto 2 Pages? I think there should be something like this?

---

### Post by SteveHillier on 2010-01-20
> **phillw said:**
> There's another programme that can read a pdf file and extract out the graphics and text into seperate files so you can manipulate them how you want to build a new page.

I did try this once using a Serif product on Windows OS.  I had created a PDF file from a DTP program.  I then shipped it to myself on another machine as the PDF.  Then when I opened it up in the DTP program on my second machine it was not good.  Articles that had been written as single text frame got unbundled into a new frame for each line of text and could no longer be manipulated as a single text frame.

It is a year or two since I did this so things may have improved since then.

---

### Post by stinger30au on 2010-01-20
pdftk *MIGHT* be able to do it

[http://www.accesspdf.com/pdftk/](http://www.accesspdf.com/pdftk/)

install it from shell

sudo apt-get install pdftk



hope this helps

---

### Post by t09 on 2010-01-21
I also thought so, but I checked through all of pdftk's features ... nope. not with pdftk. :(

---

### Post by HermanAB on 2010-01-21
Howdy,

Your best bet is probably OpenOffice.org with the PDF Edit Plugin (look for it at the OOo web site - it is there somewhere).  However, you need lots of RAM and lots of time.  It may seem that the machine hangs up so slow it goes with a large PDF file.

---

### Post by vanadium on 2010-01-21
pdfposter (or poster for postscript) is exactly intended for this. In Synaptic.

---

### Post by t09 on 2010-01-21
great, pdfposter is just what I've been looking for. 
I've installed it now,
but I can't find a manual for it and when I try to do it I get:

> /var/lib/python-support/python2.6/pyPdf/pdf.py:52: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet
/var/lib/python-support/python2.6/pyPdf/generic.py:406: DeprecationWarning: object.__init__() takes no parameters
  str.__init__(self, data)
/var/lib/python-support/python2.6/pyPdf/generic.py:216: DeprecationWarning: object.__init__() takes no parameters
  int.__init__(self, value)
Traceback (most recent call last):
  File "/usr/bin/pdfposter", line 383, in <module>
    main(opts, *args)
  File "/usr/bin/pdfposter", line 296, in main
    for i, page in enumerate(inpdf.pages):
  File "/var/lib/python-support/python2.6/pyPdf/utils.py", line 78, in __getitem__
    len_self = len(self)
  File "/var/lib/python-support/python2.6/pyPdf/utils.py", line 73, in __len__
    return self.lengthFunction()
  File "/var/lib/python-support/python2.6/pyPdf/pdf.py", line 334, in getNumPages
    self._flatten()
  File "/var/lib/python-support/python2.6/pyPdf/pdf.py", line 499, in _flatten
    catalog = self.trailer["/Root"].getObject()
  File "/var/lib/python-support/python2.6/pyPdf/generic.py", line 466, in __getitem__
    return dict.__getitem__(self, key).getObject()
  File "/var/lib/python-support/python2.6/pyPdf/generic.py", line 165, in getObject
    return self.pdf.getObject(self).getObject()
  File "/var/lib/python-support/python2.6/pyPdf/pdf.py", line 555, in getObject
    raise Exception, "file has not been decrypted"
Exception: file has not been decryptedand no output file gets created.
I guess I've done something wrong, but I cant't find a manual so I don't know what I did wrong ...

---

### Post by HermanAB on 2010-01-21
Howdy,

Try the first result:
[http://www.google.com/linux?q=pdfposter+guide&btnG=Search&hl=en&sa=2](http://www.google.com/linux?q=pdfposter+guide&btnG=Search&hl=en&sa=2)

---

### Post by t09 on 2010-01-21
I think pdfposter is just the program i need for this, but I cant't get it working. I just don't know the correct command to tell it to turn my 93 upright pages into 186 wide pages, each page split in half.

and the google-link didn't help much, i'm afraid, the first link is nothing but a downloadlink for the software, no guide or sth. there. I have it already installed, so I didn't need a dl link...

btw: Does pdfposter work correctly with multipage PDFs? i think so, but since i don't know the command to get it working, i can't check it :(

---

