---
title: "Printing PDF causes crash"
date: 2010-11-01
forum: General Help
---

### Post by juc on 2010-11-01
Hi,

I recently upgraded to Maverick and now when I try to save or print a PDF with either Firefox or Adobe Reader, Ubuntu seems to crash and takes me to the log-in screen. 

I saw that something similar had been reported as a bug and a fix released - but I can't make much sense of Launchpad and wondered if anyone knew how to get the fix? or has anyone else had this problem?

Sorry if this seems a daft question - I'm not new to Ubuntu but I'm not very techie either!  I installed Ubuntu when XP failed (rather than buy a new one) and have been running it for a couple of years and have been able to solve most things by looking up on forums...but I find Launchpad a bit daunting.

Thanks

---

### Post by gandaran on 2010-11-01
can you describe the steps you are taking to print to pdf in firefox?
and you cant print to pdf using adobe reader only make a copy of the pdf you are reading with it.

---

### Post by juc on 2010-11-01
In Firefox either click the 'print' icon or 'file-Print', I can't save a copy either and it's the same with Adobe Reader...

I can both save (a copy) and print using Document Viewer though, so I can work around it, it's just odd. I didn't have problem in 10.04.

Cheers

---

### Post by gandaran on 2010-11-01
in firefox go to file » print, in the print window choose 'print to file'
and mark the PDF radio button then on name field enter the pdf output name (pdf-name.pdf) click the bottom print button, does it crash doing this?

---

### Post by juc on 2010-11-01
No it doesn't crash - saves it as a Postcript file which prints fine. 
Sorry though - I'm not sure what you mean by 'mark the radio button'
I assume the Firefox PDF viewer is something to do with Adobe as Reader crashes as well.

Cheers

---

### Post by gandaran on 2010-11-01
> No it doesn't crash - saves it as a Postcript file which prints fine. 
Sorry though - I'm not sure what you mean by 'mark the radio button'
yes, check-mark the pdf radio buttom, unmark the postscript one or it will save in postscript file! 
> I assume the Firefox PDF viewer is something to do with Adobe as Reader crashes as well.
I don't know what you mean here, when does adobe reader crash? how are you using it?

---

### Post by juc on 2010-11-01
Hi - think I'm with you! but in the print dialogue box there isnt an option, just 'Print to File' and an advanced tab which gives you postcript options, there isn't any PDf or Postcripts buttons. I unchecked everything in the advanced settings just in case, but still saves as postcript.

Adobe Reader crashes when I try to print a PDF, or when I download and open a PDF with it (using Google Chrome as a browser), it crashes then as well. Adobe Reader will open a file that is saved on my computer quite happily, but crashes when I try and print from it.

Document Viewer is fine (haven't tried other PDF viewers).

---

### Post by gandaran on 2010-11-01
> Hi - think I'm with you! but in the print dialogue box there isnt an option, just 'Print to File' and an advanced tab which gives you postcript options, there isn't any PDf or Postcripts buttons. I unchecked everything in the advanced settings just in case, but still saves as postcript.
no pdf option! what version of ubuntu you have?
> Adobe Reader crashes when I try to print a PDF, or when I download and open a PDF with it (using Google Chrome as a browser), it crashes then as well. Adobe Reader will open a file that is saved on my computer quite happily, but crashes when I try and print from it
and what print option you are using to print, the browser file » print or the save option in adobe reader, you should use the save option (in adobe reader) when you have adobe reader opened as the print option in adobe reader only works for your ink printer.

---

### Post by juc on 2010-11-01
Hi - I've uninstalled Adobe Reader and installed a newer version. I can now use Abode to File - Print and File - Save a Copy, but if I try to use the quick print/save buttons it crashes. Also, if I use 'print to file' there is no PDF button, Adobe Reader saves as a Postscript file only.

I've tries uninstallimng Firefox again and then reinstalling trying it with each add-on disabled - still crashes.

A bit baffling, but I can work round it by using a different browser and PDF reader. Thanks for taking the trouble to help! 

 - I'm using Ubuntu 10.10 (upgraded from 10.04). Computer as Athlon64 dual, 4mb RAM and Nvidia graphics card.

Cheers

---

### Post by gandaran on 2010-11-01
> if I use 'print to file' there is no PDF button
can you post a screenshot of the print window, there should be 3 options in ubuntu 10.10, pdf, postscript and SVG, maybe you system got corrupted when you upgraded! installing from scratch is always the best way.

---

### Post by juc on 2010-11-02
There are one or two other annoying glitches.. so I decided to take your advice and do a clean install (I've upgraded from 9.10-10.04-10.10). Much better! Thanks for your help.

---

