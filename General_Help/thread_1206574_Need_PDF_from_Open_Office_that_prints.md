---
title: "Need PDF from Open Office that prints"
date: 2009-07-07
forum: General Help
---

### Post by Bladeforger on 2009-07-07
I am doing a small newsletter in Open Office and have had various problems getting output that my copy shop can use to print it.  Also, I'd like to be able to put a pdf up on our website for the half-dozen or so people that are willing to take newsletters in pdf format.

I have used 3 methods thus far:
1. Print to ps file and use ps2pdf to make a pdf file.
2. Use the CUPS pdf printer.
3. Hit the "Create PDF" button in Open Office.

All 3 methods produce a pdf file with the following properties:
Views great.
Prints gobbledygook.

I'm using Intrepid and Open Office 2.4

Any help would be appreciated very much!!!

Keith

---

### Post by bryanl on 2009-07-07
first guess is fonts.

first suggestion is to upgrade to jaunty and OOo 3,

what are you using to view the PDF? evince? then try Acrobat. check the file properties to see what it says about page size, pdf version, and so on.

For intrepid/OOo2.4 I used the cups PDF but it appears the OOo 3 pdf generation is significantly improved. I still usually use the cups pdf package in the repositories, though.

I have run a newsletter as a brochure to print on 11x17 (also a reason to use the cups PDF as I don't think the OOo pdf will 'print' to brochure signatures) and the biggest problem was the copy shop people didn't understand two sided signatures landscape.

I also print calendars to a PDF so the Office Despot print shop can run them off for a local facility. (My HP5Si is having problems).

It should work. It should be something simple. Figuring out what is causing your problem can be frustrating - been there done that. good luck. In the past I have had to go to Windows to print to pdf (after I fixed up a few artifacts from font metric differences) but lately the Ubuntu results have been satisfactory.

---

### Post by ellgor on 2009-07-07
Hi,

If you are still having problems you will be better off installing Adobe reader, here's how: 

Check to see if you have an app called "gdebi" if not it can be obtained through synaptic, once downloaded use your browser and go to the Adobe site and select the reader app, do not download the default one offered, instead click on "Different language or OS system" from the drop down menu choose Linux-86 (deb) and download it to somewhere you know you can find it. Once downloaded go to its location, right click on the package and open it with gdebi (may already be highlighted with gdebi) it will self load and be ready to use, any PDFs can then be read ,changed, printed etc, hope this helps.

Regards, Ellgor.

---

### Post by DeMus on 2009-07-07
> **ellgor said:**
> Hi,

If you are still having problems you will be better off installing Adobe reader, here's how: 

Check to see if you have an app called "gdebi" if not it can be obtained through synaptic, once downloaded use your browser and go to the Adobe site and select the reader app, do not download the default one offered, instead click on "Different language or OS system" from the drop down menu choose Linux-86 (deb) and download it to somewhere you know you can find it. Once downloaded go to its location, right click on the package and open it with gdebi (may already be highlighted with gdebi) it will self load and be ready to use, any PDFs can then be read ,changed, printed etc, hope this helps.

Regards, Ellgor.

Why so complicated?
Acroread is available in Synaptic with version 9.12 (well in Jaunty that is)
Older Ubuntu versions will probably have an older version of the Acrobat reader.

---

### Post by Bladeforger on 2009-07-07
I have Acrobat Reader.  The print shop was finally able to use one of the pdf files, good news.  That same print file gave me garbled print, bad news.

Therefore, it looks like the problem is, at least partly, in the reading of the pdf file using either Acrobat or Evince.  I tried both.  I'm going by the print shop on my way home to see how it came out on their end... and I'll update this thread.

Keith

---

### Post by Bladeforger on 2009-07-08
Here's my update:

The pdf files created, using either the CUPS pdf printer or the PDF creator built into Open Office make pdf files that are:
1. Fine for viewing on my Ubuntu computer, 
2. Print okay from a Windows computer, and 
3. Do NOT print fine from my Ubuntu computer.

Therefore, the problem seems to be with the Acrobat / Evince software when printing.  The Windows computer turns my Lucida Bright fonts into Ariel.  I'm going to try using some different fonts to see if it's a font problem.

Other files, like IRS forms, view and print as pdf files just fine.

Is it a matter of just adding some fonts that Acrobat can "see"?  Or does the Linux versions of Acrobat (as well as Evince) crunch with some fonts.

(BTW, upgrading to Jaunty and OOo 3 for the office computer isn't in the cards until Fall... got some other things to do first.  The home computer is Hardy, and that's staying Hardy for other reasons (old version of Goldrunner being one of them).)

Keith

---

### Post by mbeach on 2009-07-08
How do other things print from your Ubuntu computer? Does the source file in Open office also look garbled when printed from Ubuntu? If so, I would suspect a print driver issue.

edit: sorry I skipped over:
"Other files, like IRS forms, view and print as pdf files just fine"

---

### Post by Bladeforger on 2009-07-08
> **mbeach said:**
> How do other things print from your Ubuntu computer? Does the source file in Open office also look garbled when printed from Ubuntu? If so, I would suspect a print driver issue.

edit: sorry I skipped over:
"Other files, like IRS forms, view and print as pdf files just fine"
That's okay.  I'll clarify.  Just printing from Open Office, even large (30 + pages) files print just fine.  From Open Office, I was also trying to use the Print-->Save as file.  That creates a postscript file that prints wonderful.  Then ps2pdf makes a pdf that is perfectly viewable but that won't print on my Ubuntu box.  In fact, the garbling only happens in two cases... the newsletter coming out of Open Office and one online site:  If I go to the local real  estate tax records website, [https://www.pinellas.county-taxes.com/tcb/app/main/home](https://www.pinellas.county-taxes.com/tcb/app/main/home) , and then search real estate records, find a record, and print it... (using their "Print a copy of this bill") save as postscript works fine, going directly to the printer works fine, going to the CUPS PDF makes garbage.

---

### Post by Chronon on 2009-07-08
Obviously, it's worth figuring out the source of the PDF printing problem, but if the postscript prints fine then why not use that?

---

### Post by Bladeforger on 2009-07-08
> **Chronon said:**
> Obviously, it's worth figuring out the source of the PDF printing problem, but if the postscript prints fine then why not use that?
That's what I did for me... and the print shop was able to print from the pdf.  However, when I get a call about something that I can't see on my end (and I was worried about their being able to print at all) it would be nice to be able to say, "That's okay, it's just that way." or "Oops, let me fix it and resend."  I could dust off my old XP box and use that, but I'm trying to not even turn it on unless absolutely necessary--sometimes for weeks at a time.  I'm making a very very valiant effort to become "Windowless".

---

### Post by Chronon on 2009-07-08
I meant, why not just use postscript?  Give the shop a .ps to print and you have the identical file to view/print on your end.

Also, even if you sent them a PDF and viewed or printed a PS locally there should be no difference in content.  I have done a few conversions from .ps to .pdf using ps2pdf and find the correspondence between the two to be excellent.  Do you have a reason to suspect that your PS file would produce different output than the PDF that you sent?

---

### Post by mbeach on 2009-07-08
I'd be curious to know if you used something like scribus to create a similar pdf, if it still printed oddly.

Are you using any special gradiants in the newsletter.

Any chance you could scan or reproduce what you mean by gobbledygook. Are the characters misrepresented or is it mainly graphics, text flow that goes astray? When you tried a very simple file with 'standard' fonts did it also print in odd fashion?

---

