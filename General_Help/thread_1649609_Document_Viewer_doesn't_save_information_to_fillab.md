---
title: "Document Viewer doesn't save information to fillable pdf properly"
date: 2010-12-20
forum: General Help
---

### Post by Zorgoth on 2010-12-20
I am trying to fill out this PDF form:

[http://www.math.washington.edu/Grads/Applying/supplementalform.pdf](http://www.math.washington.edu/Grads/Applying/supplementalform.pdf)

In Document Viewer, I can click on the fields and type in them, but after spending about 2 hours writing descriptions of courses, I saved it and... it closed the document I was working on, and loading the document I saved resulted in empty fields that could no longer be edited at all - clicking on them did nothing - it looked like a blank form, except it was also broken.

Is there any way I can actually fill in this form...

---

### Post by Zorgoth on 2010-12-20
Update:  I have confirmed the problem to be this bug: [https://bugs.launchpad.net/ubuntu/+source/evince/+bug/518230](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/518230)

I really need to fill in this form, so does anyone know of a tool that will do this?

---

### Post by jmszr on 2010-12-20
Zorgoth,

You can use Xournal (should be in the repositories). You can open a .pdf via "File --> Annotate PDF", add whatever you need, then "File --> Export To PDF" or "File --> Print" .

Hope that helps.

---

### Post by jmszr on 2010-12-20
Double post - sorry.

---

### Post by Zorgoth on 2010-12-21
A workaround (from the comments on the bug I linked):

This will repair the PDF so it works properly with evince:

pdfopt "original_pdf" "fixed_pdf"

---

