---
title: "command line pdf?"
date: 2006-02-03
forum: General Help
---

### Post by closeyourwindows on 2006-02-03
is there a way take a file and export it to a pdf in the terminal.  I know open office does it and it does a pretty good job too, but I was looking for a way to do this via command line?  not super important but when you have multiple files I think it could save a lot of time.

---

### Post by spiregrain on 2006-02-04
Well closeyourwindows, it depends what sort of files they are.  For postscript files you can use "ps2pdf"- part of the "gs-common" package in Synaptic.

You can create postscript files from most apps by printing to a file- if you've chosen a postscript printer, the file will be a postscript file.

For general OpenOffice documents, [this page]("http://www.xml.com/pub/a/2006/01/11/from-microsoft-to-openoffice.html")  shows how to write an OpenOffice macro that opens any OO-readable doc and saves it as any OO-writeable doc (including PDF).  You can run OO macros from the command line, and so do an arbitrary batch conversion.  The page describes the Windows edition of OO, but I bet you can make it work with a bit of jiggery-pokery.

Hope this helps.

---

