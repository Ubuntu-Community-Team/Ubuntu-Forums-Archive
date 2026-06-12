---
title: "Printing Config - Epson Stylus DX4450"
date: 2011-03-20
forum: General Help
---

### Post by iNsOmNiOuS on 2011-03-20
Hi,

I've been having some problems recently with Ubuntu and my Printer. I find that when using ubuntu, ink drains much faster, and constant refills are required. I know the printer works fine, I use it on windows when ubuntu Fails.

Today I was trying to print a colour document out, this was with default config, standard print quality etc this was the result. On the left you can see the document before printing, and on the right the printed document. (Click to open image in new window)

[Example 1 >]("http://s4.postimage.org/fi6uztku/fail1.png")

[Example 2 >]("http://s4.postimage.org/2wujk8vyz/fail2.jpg")

How could I fix this and just get normal quality printing, without having to revert to ... windows ?

Also if anyone knows how to, how can I consult the ink levels of the DX4450 from Ubuntu. I have tried both MtInk and Epsutils and both failed

---

### Post by Script Warlock on 2011-03-20
i think your link is broken..

its not working? sudo escputil -r /dev/usblp0 -m (yourprinter) -i

---

### Post by iNsOmNiOuS on 2011-03-20
Thanks for informing me of that ! Links are now fixed

---

### Post by Script Warlock on 2011-03-20
did you tried adjusting the print quality to economy or draft?

---

### Post by iNsOmNiOuS on 2011-03-20
> **Script Warlock said:**
> did you tried adjusting the print quality to economy or draft?
Yes i did and it gets even worse, and the paper gets ripped because it gets pulled through so fast. It does a page in about 2 seconds on economy or draft, with very poor quality. I have also tried to increase the quality, but still the same type of printing error, and even more ink waste and time spent printing it.

---

### Post by Script Warlock on 2011-03-20
well that is how printing works the greater the quality the more it drains ink.. your print result is not that good I've been using libreoffice now and it seems the print quality is improving dunno if this has to do with office suites or what, btw I'm using a continuous ink system for my epson T10 on my cyber shop and i have no problem monitoring my ink levels with escputils.

---

