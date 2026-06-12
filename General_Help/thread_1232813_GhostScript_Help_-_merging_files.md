---
title: "GhostScript Help - merging files"
date: 2009-08-05
forum: General Help
---

### Post by Linix_noob on 2009-08-05
I've got GhostScript installed and I'm able to merge two PDF files into one new file.  One of the PDFs has textbox fields that users need to fill in. When I merge the two files the textbox fields are not allowing users to edit them.

Is there some option on GS that will allow me to merge the two PDFs without losing the ability to edit the fields?

The PDF with the editable fields was created in Adobe Acrobat Pro 9 and I'm calling GS from the command line through PHP. I'm using Gentoo (this is at work so I can't use Ubuntu like I do at home).

I'm using this call to GS:

gs -dSAFER -dBATCH -dNOPAUSE -sDEVICE=pdfwrite -r150 -dTextAlphaBits=4 -dGraphicsAlphaBits=4 -dMaxStripSize=8192 -sOutputFile=output.pdf 1.pdf 2.pdf

Any help would be greatly appreciated.

---

### Post by Linix_noob on 2009-08-06
Bump

---

