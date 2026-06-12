---
title: "Program to scan multi-pages to PDF?"
date: 2012-09-21
forum: General Help
---

### Post by MikeSz on 2012-09-21
Does anyone know of a program that I can use that simply scans multiple pages to a single PDF file?  

I have a Canon CanoScan Lide 100 which has its own software for Windows, which works a treat (though my windows machine has crashed) and I cant seem to find a program that will just let me scan in multi-page documents into one single PDF file.  

Anyone have any ideas?

Many thanks!

---

### Post by shreepads on 2012-09-21
AFAIK Simple Scan can do this quite easily...

---

### Post by MikeSz on 2012-09-21
Unfortunately I have tried Simple Scan as well as Xsane - Simple Scan doesnt recognise the CanoScan lide 100

---

### Post by Deepak A on 2012-09-21
**pdftk** is a nice tool to combine pdf's into one file.

**[http://www.pdflabs.com/docs/pdftk-cli-examples/](http://www.pdflabs.com/docs/pdftk-cli-examples/)**

See some examples. Install pdftk and you can create scripts to automate your work.
GhostScripts can be used with pdftk for a much better experience only if you are interested.

Deepak

---

### Post by allenc85 on 2012-09-21
gscan2pdf works for me!

---

### Post by shreepads on 2012-09-21
> **MikeSz said:**
> Unfortunately I have tried Simple Scan as well as Xsane - Simple Scan doesnt recognise the CanoScan lide 100

If your scanner is not detected, you first need to fix that, else none of the scanning utilities in Ubuntu will work...

Have you looked at this:

[http://www.sane-project.org/cgi-bin/driver.pl?manu=canon&model=lide+100&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=canon&model=lide+100&bus=any&v=&p=)

[http://bdhacker.wordpress.com/2011/04/25/canon-lide-100-scanner-in-ubuntu-with-sane-installation-permission-fixes/](http://bdhacker.wordpress.com/2011/04/25/canon-lide-100-scanner-in-ubuntu-with-sane-installation-permission-fixes/)

---

