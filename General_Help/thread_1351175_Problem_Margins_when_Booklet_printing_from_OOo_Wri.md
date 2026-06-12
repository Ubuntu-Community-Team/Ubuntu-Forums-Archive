---
title: "Problem Margins when Booklet printing from OOo Writer"
date: 2009-12-10
forum: General Help
---

### Post by Onesimus on 2009-12-10
I am having a problem printing an OpenOffice Writer document in Booklet / Brochure format.  When the document (see Document.odt) is printed in a brochure style the left hand margin begins before the page starts, so that the first 3 inches does not get printed.  I have printed this to a postscript file - the screenshot of this file is: Document (from OOo).png

I thought a possible solution would be to export the OpenOffice document to PDF, and allow Adobe Reader to print in a booklet format.  However, this is no better.  See Document.pdf  and  Document (from PDF).png

Any solution to this would be greatly appreciated, or even are the same effects reproduced for anyone else.

I am currently using Ubuntu 9.10, but have seen same effects in Ubuntu 8.10.
I am using OpenOffice: 3.1

---

### Post by Onesimus on 2009-12-14
Bump

---

### Post by Zill on 2009-12-14
Onesimus:  Your file "Document.odt" prints correctly for me using OpenOffice Writer v2.02 on Ubuntu v6.06.  Unfortunately, I don't currently have a later version available to verify if this is a "version" problem :(

If this is the *only* odt file that prints incorrectly on your system then I suggest you recheck your document format/setup.  If other files have the same problem then you may like to look at general OOo settings and your printer configuration.

The [OOo forums]("http://user.services.openoffice.org/en/forum/") may be able to help further.

---

### Post by Onesimus on 2009-12-15
Many thanks for replying.

I have other documents that do this, but only when I print in the brochure option.  If I select One page per sheet (or even two pages per sheet), it all prints fine.

I recognise that the OOo forums might be the better place - it was just a bit easier doing it here.  I didn't have to set up yet another account.

---

### Post by Zill on 2009-12-15
> **Onesimus said:**
> ...I have other documents that do this, but only when I print in the brochure option.  If I select One page per sheet (or even two pages per sheet), it all prints fine...
Just to clarify my response; I used the brochure option and printing appeared to be fine, showing full pages.
It would be useful if someone else would test this using OOo 3.1

In the meantime, you might find it worthwhile to search/post on the OOo forums as this *may* have been asked before.

---

### Post by Onesimus on 2009-12-16
The really surprising thing is that if I open the postscript files in Document Viewer, then they are displayed as the attached screenshots in my original post.

However, if I import them into GIMP, then they display exactly how they should !

Unfortunately, I am unable to attach postscript files.

---

### Post by Zill on 2009-12-16
Onesimus:  I have now tested this on my wife's Kubuntu system (Jaunty 9.04) running OOo 3.0.1.  Again, your file both printed and saved postscript files correctly (when viewed using both Evince and Okular document viewers).

We use a networked Samsung ML-4500 printer.  I can only suggest that the problem is with either your printer driver or printer/OOo configuration.

However, it is *possible* that OOo 3.1 has introduced a new bug. :(

---

### Post by Onesimus on 2009-12-16
Zill:  Many thanks for all your effort.

I think I have found a workaround (albeit botched !).  If I install cups-pdf then I can print the brochure format to a PDF document directly.

When I open the document in evince, it displays correctly.  If I print from evince, the margins are not exactly what is shown on screen (slightly bigger), but good enough to be working with.

Consequently, not sure where the bug(?) lies.  Is it in the printer driver, OpenOffice, or something else ?

Strange that GIMP is able to import original PDF document without any problems, any ideas on this ?   Thanks again.

---

### Post by Zill on 2009-12-16
Onesimus:  I am pleased that you have found a workaround at least.  From your example document it looks like you are working to a fixed deadline. ;-)

I am afraid I don't have many ideas on this one other than to see if there are similar drivers available for your printer - sometimes the installer shows multiple, slightly different, versions for any given printer type.

You could also try saving your odt file as a Microsoft Word file in OOo and then opening it with another app, such as AbiWord.  You may have to experiment to print the right brochure multi-page layout (AbiWord doesn't seem too intuitive to me!) but you *may* get it to work correctly.

Finally, you could try your file on different OS/OOo versions with an appropriate Live CD.  Setting up printing on a Live CD might be a hassle but could be worth a try and may help to identify exactly where the problem lies.

Good luck and Merry Christmas. :-)

---

### Post by Onesimus on 2009-12-16
Zill: Yep, my deadlines tend to be fairly fixed ! ;-) 

Both my printers are HP (Deskjet 930C and 4380C).  I'm beginning to feel that it may be the printer driver that might be at fault.  What printers did you try it on ?  

Merry Christmas

---

### Post by Zill on 2009-12-16
> **Onesimus said:**
> ...Both my printers are HP (Deskjet 930C and 4380C).  I'm beginning to feel that it may be the printer driver that might be at fault.  What printers did you try it on ?...
Samsung ML-4500 printer using CUPS.  PCs connected via NFS LAN.

---

### Post by girliesamuels on 2011-09-08
This is great! I found this thread really informative and very helpful.

[CENTER]________________________
**[booklet printing](http://www.simpleprint.com/bookletprinting)** |o| **[Online Printing Services](http://www.simpleprint.com/)**
[/CENTER]

---

