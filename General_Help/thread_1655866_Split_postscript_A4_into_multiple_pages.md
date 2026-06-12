---
title: "Split postscript A4 into multiple pages"
date: 2010-12-30
forum: General Help
---

### Post by Ailurus on 2010-12-30
Hi all,

I'm looking for a way to split pages from a **postscript** file. Every page in the file is a landscape A4 page with two pages side by side, each page should be split into two single A4 pages.

I found this link ([http://www.mail-archive.com/bug-ghostscript@gnu.org/msg04042.html](http://www.mail-archive.com/bug-ghostscript@gnu.org/msg04042.html)), which exactly describes how to solve it, however because of an "@-sign" in the syntax of **pstops**, not the entire command is displayed. Just read the man pages, but I can't figure out how to get it working (something with a scaling factor 2, no rotation?).

Additionally, I have a **PDF** file - every page in the file is a portrait A4 page with 4x4 pages on it. How can I split each page into 16 single A4 pages?

---

### Post by Ailurus on 2010-12-31
By the way, if somebody knows how to do this without pstops, please share as well! The point is the splitting, not the use of pstops :)

---

### Post by Ailurus on 2011-01-02
Well, after a few more hours of research, I found a way to solve both problems.

**ps2pdf** to make a PDF of the PostScript file
Use **PdfShuffler** to repeatedly crop each page and save to a new PDF
Use **Pdftk** to burst each new PDF into single pages
Use **Pdftk** to assemble all single pages of all new PDFs into one PDF file
Use **Evince** to print this PDF to a file with the actual A4 format (from A5).

The 4x4 pages on one A4 works similar, but takes considerably more time (split each 4x4 into 4 x 2x2, and then split each 2x2 into single pages). Unfortunately, PdfShuffler doesn't support terminal input as far as I know? Otherwise it would be fairly easy to write a script that does all of this :)

---

### Post by svetiev on 2011-01-12
> **Ailurus said:**
> 
Use **PdfShuffler** to repeatedly crop each page and save to a new PDF

Hi I had to do the same thing today.

I was able to select all pages and crop them all at once and then export to new pdf.

But the "crop" functions doesn't actually crop the pages it just hides one half of the page and the exported PDF with "cropped" pages is the same size as the original.

So when I put all the "cropped" pages together again (left and right side of the original PDF) I got a file twice the size of the original.

Did that happen to you too or am I missing something?

---

