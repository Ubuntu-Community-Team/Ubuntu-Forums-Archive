---
title: "pdf scan"
date: 2009-10-21
forum: General Help
---

### Post by jtmedin on 2009-10-21
Wonder if anyone has got a pdf file that is not searchable & made it searchable. Have a very long manual which says its pdf and i need to search the file. TIA

---

### Post by bwang on 2009-10-22
Are the pages image files? If so, you need to use OCR of some sort to convert it to text.

---

### Post by jtmedin on 2009-10-22
Ok i was afraid of that. I know how to do ocr from a scanner but how does one do that from a file?

---

### Post by Soundman2 on 2009-10-25
> **jtmedin said:**
> Ok i was afraid of that. I know how to do ocr from a scanner but how does one do that from a file?

Hello.  I have been researching this lately.  It appears that the state of the art, as far as free software, is to use the command line tool tesseract (tesseract-ocr in Ubuntu repositories).  Here is a (possibly dated) howto:
[http://www.howtoforge.com/ocr_with_tesseract_on_ubuntu704](http://www.howtoforge.com/ocr_with_tesseract_on_ubuntu704)

Now, since you already have the images in PDF format, you will have to first break it out into a multi-page bitonal TIFF image (or a series of individual TIFF images).  This is because tesseract cannot read PDF's directly.  Also, to reassemble the resulting file back into a searchable PDF will require a tool like gscan2pdf. (gscan2pdf.sourceforge.net), which, as I understand, may have enough integration with tesseract to drive the process from start to finish for you.

You may also want to keep an eye on the Ocropus project sponsored by Google.  They are working to build on tesseract to produce a more complete OCR system.

BTW, there are other free OCR packages, like GOCR, but it is reputed to be much less accurate than tesseract.

I have not had a chance to try these things myself yet.  Please post here what kind of results you get.

-- Soundman2

---

