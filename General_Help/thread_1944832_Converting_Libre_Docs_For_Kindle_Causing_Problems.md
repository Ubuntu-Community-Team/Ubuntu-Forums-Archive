---
title: "Converting Libre Docs For Kindle Causing Problems"
date: 2012-03-22
forum: General Help
---

### Post by demonboy on 2012-03-22
My wife is struggling with converting LIbre documents for her Kindle. She converts the .odt file to a .pdf but when she reads them on the Kindle the two things she *can no longer do *do is highlight text or annotate it. When she tries to highlight one line, a random line underneath is highlighted instead. When she annotates, the number of her note is displayed randomly too. 

The key here, she thinks, is the switch to Libre. When she was using OpenOffice she thinks the problem never happened. She's had the Kindle for two years but only had the problem since last year.

These problems do not happen with downloaded Kindle books and does not happen with pdfs created in Windows.

Any clues? Any suggestions for alternatives to Libre office? I know there are things like Calibre but I wondered if switching from Libre to an alternative wordprocessing package would be easier for my wife.

---

### Post by claracc on 2012-03-22
As you say problem didn't arise with openoffice perhaps you can try to install it instead of libreoffice.

First, you will have to remove libreoffice: [http://askubuntu.com/questions/56220/how-to-replace-libreoffice-with-openoffice](http://askubuntu.com/questions/56220/how-to-replace-libreoffice-with-openoffice).

Then you will have to install openoffice from deb package: [http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by cornouws on 2012-03-26
I would suggest to submit a bug, with a simple example, so that developers can pick it up and improve it for you and others. Also it might well be that there is a problem in LibreOffice with code from a not yet released openoffice-version.
But best, always, IMO, is to be sure first.

---

### Post by mastablasta on 2012-03-26
> **demonboy said:**
> When she tries to highlight one line, a random line underneath is highlighted instead. When she annotates, the number of her note is displayed randomly too. 
 
 
Perhaps a coversion setting is set wrong (different PDF version?!)?  What version of libre are you using? i am using previous version of it. I wonder if the e-book my wife made displays propperly on kindle. perhaps when its' ready i could send oyu a preview to check. we too made it in libre in the end as it's PDF made the total book 50% smaller size than using Adobe (admitedly i do not know how to set it up propperly) or word+pdf creator.
 
you could use sigil to edit the book in other formats, so they dispaly propperly. perhaps e-pub?! or to use sigil to see what is wrong.

---

### Post by LewisTM on 2012-03-26
As a workaround, you could try printing to a PDF. I know the results are not always the same as with the built-in PDF creator so this may work better.

Go to the Print dialog, select the Options Tab and check 'Print to file'. Click the Print-to-file button then pick a name and location.

Cheers!

---

### Post by Peripheral Visionary on 2012-03-26
I use [Xournal]("http://xournal.sourceforge.net/") to annotate pdfs. It's simple and fast. Available in the repositories.

---

### Post by demonboy on 2012-03-29
First of all, thank you to everyone who replied. I shall get on the case and report a bug with Libre Office.

LewisTM has hit the nail on the head with the idea of printing to file. This instantly solved the problem! :p

Claracc, I was interested to read your idea of installing OO through a .deb. Why do you suggest this when it is still available in Software Centre?

---

### Post by claracc on 2012-03-29
> Claracc, I was interested to read your idea of installing OO through a .deb. Why do you suggest this when it is still available in Software Centre? 

I mean you can install openoffice 3.3.0 ( [http://www.openoffice.org/download/index.html](http://www.openoffice.org/download/index.html), I think this is the spanish release, you have to look for the english one) from openoffice.org following the guide I gave. The openoffice which is in repositories (at least for 10.04) is openoffice 3.2.

---

### Post by mastablasta on 2012-03-29
> **demonboy said:**
>  
LewisTM has hit the nail on the head with the idea of printing to file. This instantly solved the problem! :p

 
 
strange that printing to file and exporting to PDF would make a difference.
 
anyway a way to transfer to e-pub format would be to bookmark the titles, save as HTML, then use sigil to line up the pictures (if there are any) and to edit it. Then you can do kindle format, e-pub almost whatever reader you want.

---

### Post by demonboy on 2012-03-29
> **mastablasta said:**
> strange that printing to file and exporting to PDF would make a difference.
 
anyway a way to transfer to e-pub format would be to bookmark the titles, save as HTML, then use sigil to line up the pictures (if there are any) and to edit it. Then you can do kindle format, e-pub almost whatever reader you want.

No disrespect to my wife but she requires the least technical, least involved solution. Printing to pdf she can manage; anything more and it becomes a headache for her. She'll just switch off!

---

### Post by LewisTM on 2012-03-29
Print-to-PDF uses the Ubuntu PDF engine while the export-to-PDF feature uses internal LO code. They usually yield the same quality but the codes are different, just look at the file sizes.

Glad it worked and that your wife is happy. Please mark as SOLVED.

---

