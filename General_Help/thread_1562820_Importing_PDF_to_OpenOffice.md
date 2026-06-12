---
title: "Importing PDF to OpenOffice"
date: 2010-08-28
forum: General Help
---

### Post by Oxwivi on 2010-08-28
How do I import a PDF files contents perfectly into OOo Word Processor?

---

### Post by Ms_Angel_D on 2010-08-28
There is a pdf extension for Open office you can download and install.

---

### Post by Oxwivi on 2010-08-28
And that extension is?

---

### Post by howefield on 2010-08-28
Try this, it's not so hard to find...

[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

---

### Post by Oxwivi on 2010-08-28
Thanks, but when open the PDF file, it asks for a password even though it's not protected.

---

### Post by Lars Noodén on 2010-08-28
> **Oxwivi said:**
> How do I import a PDF files contents perfectly into OOo Word Processor?

PDF is not for editing.  It's a container format to hold all kinds of junk on the way to the printer or the bit-bucket.  There are two things you can do with PDF: print it or delete it.  

Yes there *might* bits and pieces and even strings of text that could be recycled from a PDF, but editing is so far from the original design that it's not an appropriate use of resources to even try.  If you must edit that particular file, try to contact the author and get the original OpenDocument Format file to work with.

---

### Post by Oxwivi on 2010-08-28
It's an official document from an embassy, and they even mention that it's recommended to type if possible, and my preference as well.

---

### Post by AlphaLexman on 2010-08-28
Checkout 'unoconv' 
[http://packages.ubuntu.com/search?keywords=unoconv](http://packages.ubuntu.com/search?keywords=unoconv)

---

### Post by Oxwivi on 2010-08-29
How does it work?

---

### Post by Lars Noodén on 2010-08-29
> **Oxwivi said:**
> It's an official document from an embassy, and they even mention that it's recommended to type if possible, and my preference as well.

Ah!  There is the confusion.  It is probably a Form in which you are expected to fill in Fields rather than actually edit the Form itself.  

If it is a PDF Form, then you can use [okular](http://okular.kde.org/news.php) or about any other PDF reader to edit the fields and resave the form with the values you provided.

Again, PDF is not for editing, it is for printing or deleting.  Forms are away of tacking user input onto the printout in the right positions.  Too bad the embassy is not using XHTML forms, they risk a lot of trouble from going back to paper.

---

### Post by Oxwivi on 2010-08-29
The also provide a .doc format, but it's not rendered correctly in the OOo. Oh, and I'm using Ubuntu, it's GNOME, nor KDE. Sorry for the [all variants] tag, but I thought OOo issue would apply to all.

---

### Post by Lars Noodén on 2010-08-29
> **Oxwivi said:**
> The also provide a .doc format, but it's not rendered correctly in the OOo.


Nor in MS Office will it be rendered correctly because there are variations in the fonts and screens and configurations.  Been there done that.  It is quite frustrating.  

However, the information rather than the layout should be what is important.  It sounds like they may not quite have the web skills needed to accomplish whatever tasks.  The more I hear about PDF Forms the more I suspect they are not a desireable thing to allow to spread.  Which country's embassy, if it's not too nosy to ask?

> **Oxwivi said:**
>  Oh, and I'm using Ubuntu, it's GNOME, nor KDE. Sorry for the [all variants] tag, but I thought OOo issue would apply to all.

No problem.  

Even GNOME has a PDF reader by default, called Evince, others can be added just like on any other desktop. It does have some [forms](http://live.gnome.org/Evince/Forms) support.  You'll have to compare.

If none of the PDF Readers that you already have can work with Forms, then it is still possible to add Okular to your system.

---

### Post by Hagar Delest on 2010-08-30
If you can fill the form (try the Adobe Acrobat version for GNU/Linux, it is slower than Evince but better rendering), you can often not save the file. In this case, print it with a virtual printer like CUPS.

---

### Post by Oxwivi on 2010-08-31
> **Lars Noodén said:**
> Nor in MS Office will it be rendered correctly because there are variations in the fonts and screens and configurations.  Been there done that.  It is quite frustrating.  

However, the information rather than the layout should be what is important.  It sounds like they may not quite have the web skills needed to accomplish whatever tasks.  The more I hear about PDF Forms the more I suspect they are not a desireable thing to allow to spread.  Which country's embassy, if it's not too nosy to ask?



No problem.  

Even GNOME has a PDF reader by default, called Evince, others can be added just like on any other desktop. It does have some [forms]("http://live.gnome.org/Evince/Forms") support.  You'll have to compare.

If none of the PDF Readers that you already have can work with Forms, then it is still possible to add Okular to your system.

Regarding the .doc there is some characters (in English) missing from the heading, didn't bother checking the rest. I am sure it's not due to screen or the configuration.

And it's the Japanese embassy.

I'm pretty sure this isn't a form type PDF. Dammit, why can't I import easily, stupid PDFs...

---

