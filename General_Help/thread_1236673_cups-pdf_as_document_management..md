---
title: "cups-pdf as document management."
date: 2009-08-10
forum: General Help
---

### Post by SupraGuy on 2009-08-10
Running on Jaunty Jackelope, X86
 
First off, maybe there is a better way to do this, so I'll explain what the desired end result is, and maybe someone can suggest something better.
 
I need to be able to take a document from about any format (From a Windows network) and create a .pdf file from it for archiving and automated retrieval. The document has to have an arbitrarily assigned filename (I'm making it numeric, since that is consistent with already existing documents.) Some information is entered about the files by users into another database, so that for information regarding certain inventory, the file can be retrieved and printed, emailed or faxed.
 
What I've done so far:
 
Installed cups-pdf on the server.
 
Set up the Windows server to have a printer (HP Color Laserjet PS) which is directed to [http://linuxserver.company.local:631/printers/PDF](http://linuxserver.company.local:631/printers/PDF)
 
Edited /etc/cups/cups-pdf.conf to have a PostProcessing script, which takes the resulting filename, generates the unique numerical filename and stuffs it into the archive directory, and copies it to a user inbox, where they can look at the document, and enter the information, then delete it.
 
For the vast majority of cases, this works perfectly... Except if the original document is already a PDF, and that PDF is encrypted.
 
In this case, the resulting PDF document in the inbox is about 5k. There are 2 pages, the first is blank, and the second has an error message:
```

ERROR: undefined
OFFENDING COMMAND: ec
 
STACK:
 
{[ PDF PDFText ] </initialize exec }forall initgs }

```
 
Text for the error message all appears to be Courier, and appears to be rasterized.
 
Originally, I found that if I took the raw postscript generated from the Windows Print driver, that it would do something similar using ps2pdf.  I found a solution for this, and now ps2pdf works, and will generate a PDF from the raw file, but cups-pdf does not.  I therefore surmise that although both cups-pdf and ps2pdf use Ghostscript to generate the output, there must be a difference in the method.
 
So from this I have determined that I need to either get cups-pdf working when printing an encrypted PDF file, or I need to create a different virtual printer, where I can manipulate the raw data myself.
 
I have control over certain things.  I can ensure that the raw data will always be Postscript, and that I will not have to deal with ASCII.
 
What I need:
 
A way to create a virtual raw printer, where I can maipulate the input data as I see fit, or (prefferably) a way to make cups-pdf NOT puke when printing an encrypted PDF file.
 
What I **don't** need:
 
help setting up cups-pdf
 
Anything that can be offered would be of greate assistance.
 
Thanks in advance

---

### Post by SupraGuy on 2009-08-10
Isn't it great when you can answer your own questions...
 
Well, maybe this will help someone else.
 
The file /usr/lib/cups/filter/pstopdf is the filter for the cups-pdf printer.
 
This script has code which detects the stupid DRM crap that Adobe puts into it's postscript files and attempts to remove it, by using Ghostscript's ps2ps.  Actually rather clever, but for whatever reason, ps2ps craps out when it gets this file.
 
I found another solution to get ps2pdf to work with these files, editing (in this case) /usr/shared/ghostscript/8.64/cd /usr/share/ghostscript/8.64/Resource/Init/gs_pdfwr.ps
There is a section which looks like:
```

% Patch 'where' so that the distiller operators are only visible
% if the pdfwrite device is the current one.
{ currentdevice .devicename dup /pdfwrite eq exch /ps2write eq or {

```
I changed that to
```

% Patch 'where' so that the distiller operators are only visible
% if the pdfwrite device is the current one.
{ currentdevice .devicename dup /pdfHACKwrite eq exch /ps2write eq or {

```
By inserting the text HACK into the pdfwrite, this seems to then ignore the DRM crap.  Go figure.
 I then changed the section of /usr/lib/cups/filter/pstopdf so that it would no longer look for the DRM code at all.  Though not needed at all, I changed the entire line where it cats stuff through the DRM filter and then to $PS2PDF to the following:
```

$PS2PDF $PS2PDF_OPTIONS $ppd_opts $infile -

```
Thus ignoring the $DRMFILTER value entirely.
 
This works.
 
I have the following concern:
 
Upgrading.  If I update Ghostscript and/or cups-pdf this is liely going to break again.  Not fun.
 
It seems that the cups-pdf printer had something in place to look at this.  I don't know why it breaks.
 
Anyway, hope this works for people.

---

### Post by SupraGuy on 2010-03-16
Well, for what it's worth, something in the updates did break that solution, so I had to re-do it.

---

### Post by Jose Catre-Vandis on 2010-03-16
Interesting Approach, nice solution, best marked as solved?

---

