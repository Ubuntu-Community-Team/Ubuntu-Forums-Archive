---
title: "Cups: Large Files do not print"
date: 2010-11-29
forum: General Help
---

### Post by Markus Zimmermann on 2010-11-29
Hi all,

i have a problem with cups on a lucid/64 machine. 

"Unable to write print data: Broken pipe"

The pdf-file to print has a size of 4,7MB. After sending the file to the printer the size of the file is more than 18 MB.

We use a Xerox WorkCentre 7232 which is via

socket://ip_adress:9100

connected to cups. The same configuration had been working fine for several years with hardy.

Cups refuses to print large files. When splitting up the print-file all works fine. Does anybody know how to solve this problem. I googled a lot and it seems that other users do have this problem also.

Any hints?

---

### Post by garethfoxwilliams on 2011-05-25
I have similar problems. both on Lucid Ubuntu and Natty Xubuntu. 

Today's example: A 3 page PDF. 

Total size 2164k - whole document takes a while to process, then Print Status says job completed, but it has not printed and just disappeared.

Page 1 on its own - 1840k - does not print, as above
Pages 2 and 3 231k and 123k  - print quite happily.

the printer is HP Business Inkjet 2280 on a network, with the standard 32MB memory.

Any help or suggestions gratefully received.

---

### Post by garethfoxwilliams on 2011-05-27
bump

---

### Post by huangweiqiu on 2011-05-27
same issue ,subcribe

---

### Post by flint_ on 2011-07-23
I am sending rather large files through cups and getting nowhere.  Some printers let you upload pdf files to them and then they handle the pdf.

If I knew what page limitation I had on the printers, I could use pdftk to custom the size to fit.  I am gonna try to fix it this way.

Flint

---

