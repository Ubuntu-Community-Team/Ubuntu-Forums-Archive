---
title: "no error, but not printing"
date: 2010-12-09
forum: General Help
---

### Post by travelour on 2010-12-09
I'm running 10.04 on a Fujitsu FMV Biblo MG/A50 in Japan. 

I added a network printer (Epson LP S3000) to socket://10.3.3.179:9100 .  Everything seemed to go just fine.  The paper settings are A4 size.  

When I test print (from CUPS GUI and system admin printing), the job goes into cue and then goes away as if it printed.  Only problem, nothing actually printed.  No error messages.  Nothing.  I ran troubleshoot and it couldn't ID a problem.  I also tried printing from firefox and Open Office Docs.

I was able to print from this computer at my old work site, but that was on 9.10, a different network and different printer models.  I have also installed 8.04 and cannot print from there either.  Any ideas?

---

### Post by wei2912 on 2010-12-09
You may need to install a driver for your network printer. Search for it on google and download the driver for debian, which ubuntu is based on.

---

### Post by travelour on 2010-12-09
Thank you Wei.  I downloaded the ppd, but no luck.  The foomatic webpage gives the following note with the ppd.  I don't know which ghostscript this uses though or how to get that info.  
Guess I should note that I am a novice and don't really know what I'm doing.  

*******************
All Japanese model Epson laser printers understand ESC/Page or ESC/Page-Color. Epson provided thise languages driver, and gives some additional options to the supported printers.

The driver serves for black-and-white laser printers (Ghostscript output devices "lpXXXX") as well as for color laser printers ("lpXXXXc"). It does not support the Epson EPL "L" series. There you have to use the third-party driver "epsonepl".

Here some hints for older versions of the driver:

Version 1.0.4 of this driver works only with Ghostscript 5.50, not with Ghostscript 6.5x and newer. For the new Ghostscript versions use this patch from Crutcher Dunnavant (Red Hat).

Version 3.0.2 is prepared for both Ghostscript 5.x and 6.x. For Ghostscript 7.x or newer a small fix is needed: Execute the following command line in the main directory of the unpacked driver source package:

perl -p -i -e "s/GS_VERSION_MAJOR\s*==\s*6/GS_VERSION_MAJOR >= 6/" gdevescv.c gdevesmv.c

Then the driver also compiles with these versions of Ghostscript.
**************

---

