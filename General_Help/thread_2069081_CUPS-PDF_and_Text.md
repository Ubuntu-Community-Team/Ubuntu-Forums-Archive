---
title: "CUPS-PDF and Text"
date: 2012-10-10
forum: General Help
---

### Post by pastim on 2012-10-10
I have some reports I would like to print to PDF, rather than paper, so I can carry them around.  They are mostly text, and I have to be able to search them for text strings.

Currently it seems that the output of CUPS-PDF is not searchable.  I am on Ubuntu 12.04, 64 bit, all latest stable uodates.

I am aware that several programs, including chromium and Libreoffice have their own pdf printing capability, which does produce searchable documents.  This solves the problem for many types of report.  However, herein also lies the main wrinkle.

The reports I want to produce are from MSAccess 2003 under Wine (currently 1.5.9). CUPS-PDF is available as a printer, but suffers from the problem stated above.  I have tried installing several pdf creation programs under Wine, but none seem to work.  PDFCreator got closest - I have a clean installation, a printer is defined, the program seems to print to it - but I cannot get it to actually produce the files.

Ideally I would prefer to use CUPS-PDF rather than more Wine kludges.  I have searched many places for help.  All I have found is a number of bug reports which appear to still be open, and some references to earlier versions of CUPS-PDF that might work (if I could find them).

Some may ask why I don't use LibreOffice Base or some other database instead of Access.  The reason is that I have a really well-developed application in Access which would take me months to replicate under any other (free) platform.  Even If I did expend this effort I am not sure I would get anything as sophisticated, both in terms of the GUI and the complexity of reports I can produce. So for now at least I need a way of printing to text-searchable PDF from a program under Wine.

Any ideas?

---

