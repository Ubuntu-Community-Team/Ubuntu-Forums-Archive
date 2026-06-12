---
title: "Help with Scanning OCR Docs"
date: 2010-06-04
forum: General Help
---

### Post by Dyffo on 2010-06-04
Hi there - this is a cry for help if anyone has any experience of scanning documents.  I have a printed PDF Document which is comprised of Text, Lines, Boxes and so forth. I need to edit this document.
I have scanned using varying forms of OCR software, the text reproduces fine, this I can edit - fine , but I cannot seem to save and reproduce the lines and boxes which is equally important. I should say that this PDF doc is also available on file on my USB stick.
Help please.

---

### Post by ajgreeny on 2010-06-04
I suspect you will be unlucky with your wish for OCR that will do anything other than with plain text, and that has to be scanned as a **tif** file if you use the best available application so far in linux, which in my opinion is tesseract.  I find gocr a waste of time and incredibly inaccurate.

There's at least one proprietary application available now called Abbyy Finereader, but it's expensive for most users at 149euro.  I have no idea about the use of anything else, perhaps through wine, but as windows has many OCR apps available it could be worth a look at the wine app database.

---

### Post by StuartN on 2010-06-04
> **Dyffo said:**
> I should say that this PDF doc is also available on file on my USB stick.

Why would you wish to OCR a document that you already have in electronic format?

Is there a reason why you don't use a PDF editor, a PDF import or a PDF converter?

---

### Post by ajgreeny on 2010-06-04
That's a very good question which I didn't think of when I replied.

Perhaps the pdf is a simple image rather than a text and image combination.

---

### Post by Dyffo on 2010-06-04
> **StuartN said:**
> Why would you wish to OCR a document that you already have in electronic format?

Is there a reason why you don't use a PDF editor, a PDF import or a PDF converter?

This is what I am looking for a PDF converter/ Editor , is there one for Ubuntu.

What I have is a   manual in PDF format,Scanned and saved in PDF on to my USB Stick I wish to modify some of the text to update it. My originals used to compile the Doc have long gone.

---

### Post by StuartN on 2010-06-05
> **Dyffo said:**
> This is what I am looking for a PDF converter/ Editor , is there one for Ubuntu.

There is a Sun PDF Import extension for Open Office, but some people say that KWord's import is more reliable. I ran a couple of PDF manuals through Calibre into EPUB format, which is easy to edit.

There are pdftotext, pdf2ps and plenty of other command line tools - they are probably far better if you are aiming to rebuild a lost source file to regenerate the PDF.

---

### Post by Dyffo on 2010-06-05
ALL SORTED. I found two solutions the first was PDF Editor   (Synaptic ) - and the BEST of all was "PDF ESCAPE" which is an  ONLINE free CONVERTER - MAX 50 Pages - but excellent - no messing.

---

