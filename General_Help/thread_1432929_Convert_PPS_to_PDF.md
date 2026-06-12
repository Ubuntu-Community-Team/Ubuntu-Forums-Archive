---
title: "Convert PPS to PDF?"
date: 2010-03-18
forum: General Help
---

### Post by DedMoroz on 2010-03-18
Hi there! I am trying to convert a PPS file that was emailed to me, into a PDF file. In OO Presentation there is even a nice feature to do this, but the option is grayed out after I open this PPS. I also cannot edit or save this PPS either. Ive checked the files permissions, but it all appears as if I can edit it.

Any other way to convert, like in terminal? Thanks for ANY help!

---

### Post by srs5694 on 2010-03-18
Can you print it? If you can print it, try locating a "print to file" option. In OpenOffice.org, the print dialog box has a "print to file" checkbox that's easy to overlook. If you can print to a file, the result should a a PostScript file (with a .ps extension, or possibly whatever extension you give it). You can then convert that to a PDF with a tool called ps2pdf (or possibly pstopdf; I've seen both). Normally, you just feed it the PostScript file, as in "ps2pdf foo.ps". This results in a like-named PDF file (foo.pdf in this example).

---

### Post by jrssystemsnet on 2010-03-18
> **DedMoroz said:**
> Hi there! I am trying to convert a PPS file that was emailed to me, into a PDF file. In OO Presentation there is even a nice feature to do this, but the option is grayed out after I open this PPS. I also cannot edit or save this PPS either. Ive checked the files permissions, but it all appears as if I can edit it.

Any other way to convert, like in terminal? Thanks for ANY help!

Open it up in OpenOffice, print, select Print to File, click the PDF radio button for the output format, and Bob should be your uncle.

---

