---
title: "ps2ps changed behaviour between Ubuntu 9.10 and 12.04"
date: 2012-09-03
forum: General Help
---

### Post by ColinBrough on 2012-09-03
I use 'ps2ps' (from ghostscript package) to clean-up some locally produced PostScript and send it my printers.

The output of 'ps2ps' used to print OK on my networked Kyocera
FS1028MFP postscript printer. Now I get long delays (10 minutes!) to print and blank
pieces of paper. Worked fine with the version/setup from Ubuntu 9.10; stopped working on upgrade (fresh install) to Ubuntu 12.04.

Other printing (output of dvips, LibreOffice, Mozilla, Thunderbird,
etc) all works OK.

As far as I can tell the printing subsystem is sending the raw
postscript to the FS1028. Printing to my HP Photosmart 7850 (USB) is
working fine.

Ubuntu 12.04 ships with ghostscript version 9.05. Not sure what was on Ubuntu
9.10, nor what may have changed in the printing subsystem.

Any thoughts on tracking down what is going wrong?

---

### Post by ColinBrough on 2012-09-03
Intriguingly 'ps2pdf' works... ie

ps2ps file.ps - | lpr                      Fails to print
ps2pdf file.ps - | lpr                    Prints OK

What is lpr doing with that postscript?!

---

