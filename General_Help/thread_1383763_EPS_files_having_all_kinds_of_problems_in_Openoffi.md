---
title: "EPS files having all kinds of problems in Openoffice Impress 3.1"
date: 2010-01-17
forum: General Help
---

### Post by lethalfang on 2010-01-17
First of all, every time I open an Impress ODP file that contains lots of EPS files, it'll take many minutes to fully load. 
TOP command in the terminal shows lots of CPU being used in gs (ghostscript) and convert. 
Even after 10 minutes, SlideShow often does not show any of the EPS figures in my slide. I have to do strange things like making some random editing in the ODP file, undo the editing, and then Save the ODP file again, for the SlideShow to show the EPS files. 
That is a problem in all 3 of my Ubuntu 9.10 computers. 

Anyone has had this problem before? Got a fix?

Thanks.

---

### Post by lethalfang on 2010-01-20
Any ideas? Any similar problems?

---

### Post by cyberey66 on 2010-05-13
> **lethalfang said:**
> Any ideas? Any similar problems?

I've noticed this as well, it is a bug in open office.  The software renders the vector based graphics (like EPS) each time they are displayed.  The only fix for this is to use non-vector based graphics such as JPG.  For presentations, you can just export for PDF.

I use vector based graphics in writer and it brings my 8GB ram, 3GHz quad core computer to a halt.

If anyone has any other workaround, I'd be happy to hear it.  I would be nice if open office could just render a preview of each vector based image when the document is loaded.

---

