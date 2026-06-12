---
title: "printing to PDF"
date: 2009-10-16
forum: General Help
---

### Post by DeltaFee on 2009-10-16
Hi I have ubuntu 9.04, and I been trying to get cups-pdf working correctly, I installs cups-pdf, and my ubuntu created the printer but whenever I try to print through it, it seems to fail printing.

---

### Post by abhishek.malhotra35 on 2009-10-16
Can you let us know in detail what kind of issue are you facing? What kind of error do you get while printing?

---

### Post by suomaf on 2009-10-16
I have also installed cups-pdf on jaunty ubuntu netbook remix. The priniting seems to finish correctly but I cannot find where the pdf file goes. Any help?

---

### Post by suomaf on 2009-10-19
bump

---

### Post by DeMus on 2009-10-19
> **suomaf said:**
> I have also installed cups-pdf on jaunty ubuntu netbook remix. The priniting seems to finish correctly but I cannot find where the pdf file goes. Any help?

From which program do you print? Do the pdf files not appear in your home folder? Maybe a hidden subfolder. In Nautilus switch on the hidden files and folders with "ctrl h"

---

### Post by mike555 on 2009-10-19
Unless you set a name it saves as "  .pdf  "so it would be hidden in your home folder.

next time set a name before the "  .  "

---

### Post by suomaf on 2009-10-19
Thanks for the reply guys, but I cannot find any hidden folders or .pdf file in my home directory. It is a fresh install of cups-pdf. Is there any conf file that I need to edit?

Thanks for the help

---

### Post by mcduck on 2009-10-19
> **suomaf said:**
> I have also installed cups-pdf on jaunty ubuntu netbook remix. The priniting seems to finish correctly but I cannot find where the pdf file goes. Any help?

cups-pdf has a certain built-in destination directory where it outputs te pdf files. If I remeber right, that would be ~/PDF, which you have to create yourself.

Anyway, have you tried the built-in print-to-PDF function? Just set "Print to file" as the printer in the Print dialog and set output format to PDF (no cups-pdf required)..

---

### Post by suomaf on 2009-10-20
Thanks creating the PDF directory in home did it.. Wierd though, when I tried to edit the /etc/cups/cups-pdf.conf and change Out ${HOME}/PDF to anything it does not work.. The only option works with ${HOME}/PDF

The built-in pribn-to-PDF function works just fine. Thanks for showing me that.

Cheers

---

### Post by DeltaFee on 2009-10-20
Sorry been away from my comp. "terrible Cold" What I was trying to do is setup a print-pdf Server for all the computers on my network. which is why I not sure if > pribn-to-PDF function would be good solution. The error says > Printer Status: idle /.../ Failed

---

