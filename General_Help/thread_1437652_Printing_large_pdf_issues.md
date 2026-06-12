---
title: "Printing large pdf issues"
date: 2010-03-24
forum: General Help
---

### Post by ColdFFF on 2010-03-24
I have an issue printing large pdf files (example: 24MB, 568 pages) via a number of pdf viewers.

The computers in our office are all running Karmic 64bit, and the printer in question is an Oki C9850 MFC. I will admit that there is no officially supported linux driver for this printer, nor is there a ppd available from OpenPrinting. I managed to pull together a driver by extracting the ppd from the officially supported Mac driver and making a few tweaks - its not perfect (in the sense that 2 ppds are required, one for single sided and one for duplex) but printing DOES work correctly for smaller files.

The issue comes up only with larger files. With the example given above, printing with evince, the printer queue shows the job as "Processing - Printer Not Connected?" and will occasionally print the first page single sided, though often the job times out on the printer after 15 minutes. Printing with Adobe Reader is normally quicker, but again will only print the first page single sided.

Checking the job log on the printer shows these attempts to print the file with either an Error or Cancelled status, with the document size coming in at **1103MB**.

From all this, you are probably thinking to yourself "Well obviously the printer cant handle this job", or "The pdf is corrupted" or similar. However, I have been able to print this file. Using xpdf the file printed perfectly, although still took a long while to spool locally. Printing using the lpr command also printed perfectly, and was much quicker. To me this shows that it is not really an issue with the printer or the pdf.

If it were up to me, I would have no problem using xpdf or printing from the terminal, however, it is not, nor can I cope with the complaints from everyone in the office for having to use xpdf, and mention of the word terminal is normally met with a blank expression.

Are there any ideas on how I can get evince or adobe to print files like this correctly in the future?

---

### Post by DawieS on 2010-03-24
Did you have a look at the various customizing options of CUPS? It seems as if it is possible to generate your own printer driver, fully customized for a specific set-up. Visit **[http://localhost:631/](http://localhost:631/)** in your Internet Browser for more information.

---

### Post by cristianrosa on 2010-05-17
Hey thanks for the tip of directly using lpr, I was having the same problem with a 7.7 Mb Pdf (80 pages).

---

