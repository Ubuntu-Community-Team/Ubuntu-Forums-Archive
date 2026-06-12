---
title: "Bank of America PDF statements will not print"
date: 2010-11-12
forum: General Help
---

### Post by edwardp on 2010-11-12
Ubuntu is unable to print Bank of America customer account statement PDF files, this occurred on two different systems both 32- and 64-bit installations).

The printer on the 32-bit system (DeskJet 932C) flashed the error light (amber) and when the error cleared, it printed a garbage page:

> 
Error:  /undefined in --run--
                             Operand stack:
                                              --dict:7/16(L)--     File
                                                                       Execution st


The printer on the 64-bit system (Deskjet D1420) did not print anything.

This seems to be limited to the account statements as all other PDF's will print without trouble.

Has anyone else seen this?

---

### Post by AlphaLexman on 2010-11-12
Have you tried different pdf viewers, evince, adobe (etc.)?

What do you get from:
```
file bank_of_america.pdf
```

and, take a look at: 
```
man pdftk
```
Of course you don't want to upload your bank statement so others can test it!

---

### Post by edwardp on 2010-11-12
~$ file bofa.pdf
bofa.pdf: PDF document, version 1.3

~$ man pdftk
No manual entry for pdftk

[B]EDIT:  It will print the PDF successfully, from page 2 onward.  

If an attempt is made to print all of it beginning with page 1, or to print page 1 by itself, that is when it fails.  There is something about page 1 that it doesn't like.
[/B]

---

### Post by AlphaLexman on 2010-11-12
Just to eliminate a mozilla problem, can you print other pdf's from your browser?

---

### Post by edwardp on 2010-11-12
It will print other PDF's perfectly.

---

### Post by AlphaLexman on 2010-11-12
Check out 'pdfinfo' I don't know if it is installed by default.

---

### Post by edwardp on 2010-11-12
I just installed "xpdf" and it is printing, although some data at the far left of the pages are chopped off and there isn't anything in xpdf to change settings.

This would appear to be an Evince issue.

PDFINFO just lists the author, creator, number of pages, page size, file size, PDF version 1.3, etc.

---

### Post by oldsoundguy on 2010-11-12
Don't always blame YOUR software.

Many a site is screwed up because of the IT that entered that data did not cross platform check their work.  Even though IE is less than 50% in world wide usage now, many an IT will only check their work in IE and no other browser platforms!

---

### Post by edwardp on 2010-11-12
I downloaded/installed Adobe Reader 9 for Linux from Adobe's web site, it is printing it perfectly.

---

### Post by stephenesherman on 2011-03-05
I found that xpdf permitted me to print my bank pdf's.  Like the original poster, I could print most pdf's, but not the one from my bank (Citibank). I tried the "print from page 2 approach," but that didn't work.

Installed xpdf, which has a very old-fashioned looking GUI, .. but it worked! (I did not see Adobe Reader in Ubuntu's Synaptic Package Manager, which is  my preferred source of software.)

I am running Ubuntu 10.10 on a Dell Inspiron 530s, using an HP Officejet 6500.

---

