---
title: "Print issues with ML-1750"
date: 2012-06-24
forum: General Help
---

### Post by maxxfi on 2012-06-24
Hello,

I recently upgraded my desktop to Ubuntu 12.04 from 11.04. The PC is connected to a Samsung printer ML-1750 which was working ok (with the cups-gutenprint-simplified PPD) while on Natty. 

Now, the prints (at least from pdf) are not so reliable: if I have a 2 pages document, I turn on the printer, print (e.g. with evince) 1st page only, then issue a new command to print 2nd page, the 1st page is perfect, the second one is often garbled (the printout looks like a distorted 20x zoom of the content). 

The weird thing is, as from CUPS administration I set it so that the print jobs are not discarded immediately after the print, if I re-print the same botched job... the result is now ok!

Perhaps the first print leaves the printer in a wrong state, so that the following job gets corrupted? 

Any idea how to debug the problem?

The printer is showing the same issue with the 'default' Ubuntu Precise PPD and with the latest cups+gutenprint PPD, which I'm currently using:
*NickName:      "Samsung ML-1750 - CUPS+Gutenprint v5.2.8-pre1"
*cupsFilter:    "application/vnd.cups-raster 100 rastertogutenprint.5.2"

---

### Post by kerrsmith on 2012-07-10
I have exactly the same problem except I performed a new install. The printer was working fine on 11.04 but in 12.04 it prints lots of pages of junk with the recommended driver and with the gutenprint driver it prints the first page fine then all other pages extremely large and distorted.

Did you find a solution to this, my only option at the minute seems to be to go back to 11.04 as I do lots of printing and need this to work as it used to.

---

### Post by maxxfi on 2012-07-10
No I did not find yet a solution.
So far as 'workaround', either I reset the printer after every page, or I send the print via a virtualbox machine running older Ubuntu or Win.

---

