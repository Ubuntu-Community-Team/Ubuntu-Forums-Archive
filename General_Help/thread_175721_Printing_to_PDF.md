---
title: "Printing to PDF"
date: 2006-05-13
forum: General Help
---

### Post by jonnymccullagh on 2006-05-13
I've been using Kubuntu for a few months and this is something I miss. 
I want to be able to 'Print to PDF' from all applications.
I have noticed that KDE programs seem to have the Print to File (PDF) option. But I feel I should be able to print from Gnome programs too as if the PDF printer was a real printer on the system.
For example, Firefox because it is not properly integrated into Kubuntu does not allow PDF printing (I can use Konquorer but there are not always KDE equivalents to Gnome programs).
I would also like to be able to choose the filename and location. 
Any thoughts?
thanks,
jonny

---

### Post by tonyr on 2006-05-13
I don't know the answer, but I'll speculate.  The utility **ps2pdf** will translate
PostScript output to PDF.  CUPS (your favorite print manager) might have
a way to set up a program to look like a printer.  I've seen this in the past
in other print manager systems.  I really don't know that much about CUPS
features, but this sounds like an interesting line of investigation.

I used PostScript as an example because **firefox** will write PostScript
when you have selected **Print->Print-to-file**.

If such a thing were possible, you would have to find out what format each
application prints, if it prints-to-file at all, and make a special printer for each
output format.

---

### Post by tonyr on 2006-05-13
[QUOTE=tonyr]CUPS (your favorite print manager) might have
a way to set up a program to look like a printer. [/QUOTE]

Oh Yeah!  Google for **cups "print to file"**.

---

### Post by asimon on 2006-05-13
It should be possible to setup a pdf printer via the cups-pdf package. But I never tried it.

---

### Post by treris on 2006-05-14
There is also another way to print to pdf in FF, you can edit the printing command for a pdf printer in about:config

here's the link with an explanation, I used this and it works like a charm

[http://www.ubuntuforums.org/showthread.php?t=7827&page=3](http://www.ubuntuforums.org/showthread.php?t=7827&page=3)

hope that helps

---

### Post by jonnymccullagh on 2006-05-14
Thanks folks,
I got that working in Firefox but then tried going to the K Control Panel and Printers
Add Printer/Class - Next
Then chose "Other Printer Type" - Next
Scrolled down to File - Virtual Printer [PDF Printer] - Next
Under the list of manufacturers I chose Postscript Printer - Next Next Next etc
Finally I gave it a name e.g. CupsPDFPrinter

This gives me a PDF printer in Gnome applications too so I am relatively happy for now. It would be good if Linux distributions came with is as standard - it is not perfect but all it really needs is an option to choose the file name and location. 
Next I need a PDF Editor - but I think that will be harder.
cheers,
jonny

---

### Post by jetpeach on 2006-05-23
Yeah, it would be nice if all applications would show the same printer list, including the print to PDF option...

---

