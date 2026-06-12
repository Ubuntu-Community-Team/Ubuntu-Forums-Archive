---
title: "Large file size with xsane save to PDF"
date: 2011-06-17
forum: General Help
---

### Post by Magnificent 7 on 2011-06-17
CanoScan LiDE 210 running under 10.10 on a Tosh Tecra M11-130 laptop.

Currently trying out xsane to archive some paperwork in monochrome, as the bundled Simple Scan utility can only save in either colour or greyscale. The problem is that the same A4 page saved as monochrome has a file size about three times larger in Ubuntu than in Windoze.

The scan mode options are either 'Colour', 'Greyscale' or 'Lineart'. There is no 'halftone' setting available, as shown in some of the xsane manuals. Don't know whether this is significant to this issue.

Xsane's main option window shows 3508 x 2480 x 1 bit for a 300 dpi A4 monochrome scan when 'lineart' is selected, but the intermediate file size is 8.3MB instead of just over 1MB before packing for the PDF. This is consistent with each pixel not being recorded as a 1 or a 0, but as a greyscale 11111111 or 00000000, i.e. monochrome/halftone, but stored in an eight bit field.

Any ideas how to tweak xsane for true monochrome intermediate .pnm files and saved PDFs?

---

### Post by tredegar on 2011-06-17
I just tried this.
10.04LTS
xsane 0.996
Canoscan LIDE20

Selected Lineart at 300DPI. Scanned A4. Result 2444x3467x1
File saved is **out.pnm** and is 1061038 bytes, which is about right.
I saved the file from the "Scan viewer" window.

Are you sure you do not have "Greyscale" selected?

---

### Post by Magnificent 7 on 2011-06-17
Thanks for that. Yes, definitely not in greyscale mode. I can get the same result saving from the viewer window.

In a side-by-side comparison, a fairly busy A4 sheet scans to 1MB of .pnm or 98k of TIFF. Now using image viewer or GIMP to open this TIFF and printing to file, selecting .pdf format, results in a file that grows to 172k in size.

Importing the same 98k TIFF as a picture into OpenOffice Word Processor, expanding up to fill the page and exporting as pdf results in a file of 78k, which feels about right for the same page scanned at 300dpi halftone using the Windoze drivers.

Something in the toolchain involved with creating and saving pdfs from a monochrome image is re-expanding the intermediate files, probably back up to greyscale, for manipulation.

---

### Post by tredegar on 2011-06-17
> I can get the same result saving from the viewer window.
Errr, this means you get the same as myself (1MB file) or same as you (8MB file)?

As for importing / exporting / PDF-ing I'm not good at the mathematics behind this. I think "converting" images to PDF just embeds the image (perhaps in it's original format?) into the PDF "container". A bit like AVI isn't a format, but a container for AV codec specifications, and binary data, as I understand it.

Opening out.pnm with gimp and saving it as out.tiff (with LZW compression) reduces its size to 184kB, saving it as a jpg leaves the size at the original 1MB. Re-opening this 184kB tiff with gimp and saving it as another pnm increases its size to 8MB. Image quality across all formats appears, to my untrained eye, to be identical.

Slightly off-topic, but a doc created with MS Word, opened in OOWriter and resaved (unaltered) as a MS doc is about 25% of its original size. MS can still open it though. Strange.

But I am no expert at any of this. Image-encoding and AV codecs are pretty much a mystery to me. I think you'll just have to experiment, and find out what works best for you. 

Good luck.

---

### Post by Magnificent 7 on 2011-06-17
> **tredegar said:**
> Errr, this means you get the same as myself (1MB file) or same as you (8MB file)?

Yep, I get the same as you, i.e. a 1MB .pnm file. I guess unless anyone else has any suggestions, I'll have to import TIFFs into successive OO word processor pages, rescale each image manually then export to pdf to get a multipage document.

Clunky, but even with all the font, setup and formatting junk that exporting from the word processor must embed, the PDF you get from the OO export is less than half the size of printing a direct pdf from xsane or GIMP/Image Editor etc. And if anything it looks sharper too.

OO must have its own routines for creating a pdf, whereas the others are accessing some kind of printer driver functionality that is creating the monochrome -> greyscale bloat.

---

### Post by rayerta on 2011-07-29
Simple Scan produces 50k pdf files with better readability than the line art on XSane (which even at 100dpi produces a file larger than 200k).

If you want to make a multipage doc, try using pdftk from the command line to combine multiple pdf's into one.

---

