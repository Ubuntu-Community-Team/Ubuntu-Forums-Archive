---
title: "print two landscape pages per portrait sheet"
date: 2009-08-27
forum: General Help
---

### Post by misha680 on 2009-08-27
I have tried both mpage and psdup but they don't really
seem to do it.

I have a pdf:
[http://people.hnl.bcm.edu/misha/tmp/tmp.pdf](http://people.hnl.bcm.edu/misha/tmp/tmp.pdf)

I would like to print it so that two pages exactly fill up one 
portrait sheet. Acrobat shrinks pages, Evince almost does this but
the pages are left-justified, any hints?

Thank you
Misha

---

### Post by tgalati4 on 2009-08-27
In a terminal:

sudo apt-get install posterazor
posterazor

This is for large posters. 

 
Edit:  After viewing the slides, perhaps xpdf might do it.  Sometimes older is better.

sudo apt-get install xpdf
xpdf yourslides.pdf

---

