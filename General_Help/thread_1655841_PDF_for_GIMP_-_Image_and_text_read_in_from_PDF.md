---
title: "PDF for GIMP - Image and text read in from PDF"
date: 2010-12-30
forum: General Help
---

### Post by tstolber on 2010-12-30
Hello

I have a project where I need to modify (add a customer specific footer) a whole bunch of PDF files.

On my Windows PC with Corel draw I can pull in the PDF files, change the missing fonts etc and then add in the footers and logos that I need to and then export as PDFs and that job done.

I would like to be able to do the same thing with my Ubuntu system using GIMP. It seems like it should be able to do it but I can´t figure out how at the moment. I have looked around and haven´t found anything conclusive.

What I would like to be able to do is to open a PDF in GIMP (or any other suitable program for Ubuntu) and be able to move the text and elements around, modify text and add in sections just like I can with Corel Draw.

Its important that when the PDF is exported the meta data is available and that the text is indexable by search engines, not just an image of all of the textual content on the page.

Thanks in advance for any help.

Best Regards

Trevor

---

### Post by ajgreeny on 2010-12-30
I've never used GIMP for PDF editing, but have used the extension for OpenOffice which is reasonably good, though formatting is sometimes a problem on complicated PDFs.

Go to [http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport) to get it and have a play.  It will open the PDFs in OOo-Draw normally, and you can use the toolbar at the bottom of the Draw window to edit.

The repos have a package called pdfedit, but if you can get it to do anything worthwhile you're a better user than me.  I'll be very interested to hear if you do try pdfedit and manage to get it to work.

EDIT:
I've just tried the updated version of pdfimport, 1.0.4, from Oracle, instead of the older version 1.0.1, I had from Sun.

I can not get the new version to import anything into OOo, but have not had time to look into the problem further.  I have now restored the older version 1.0.1 which still works.

---

### Post by qamelian on 2010-12-30
GIMP would equate to Corel Paint, not Corel Draw. Corel Draw is a vector graphics program, so you're probably looking for something like Inkscape, which will load PDFs through File > Import.

---

