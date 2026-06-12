---
title: "OpenOffice issues with KDE integration"
date: 2010-02-09
forum: General Help
---

### Post by oshunluvr on 2010-02-09
OOCalc was crashing on my system every time I tryed to change sheet sequence in a workbook using drag. Meaning: I click-drag a sheet forward in the workbook to a new location and drop it - then OO immediately crashes. On a multi-cell select and move operation on a sheet, the crash and console output from the crash is the same.

After posting and getting advice on the OpenOffice forum, the problem was solved by removing the **openoffice.org-kde** package. If anyone knows a fix while still using this package, let me know.
  

Here's the console error output:
Nothing found in logs. 
Error output from console (SAL_SYNCHRONIZE=1): 
 
QPixmap: It is not safe to use pixmaps outside the GUI thread 
QPixmap: It is not safe to use pixmaps outside the GUI thread 
QPixmap: It is not safe to use pixmaps outside the GUI thread 
QPainter::begin: Cannot paint on a null pixmap 
X-Error: BadDrawable (invalid Pixmap or Window parameter) 
        Major opcode: 62 (X_CopyArea) 
        Resource ID:  0x0 
        Serial No:    58776 (58776) 
 
Only difference in the console output is the Serial No. which changes at every crash. Single cell moves and moving sheets via pop-up menu does not result in a crash. 
 
System info: 
Kubuntu 9.10 Karmic Koala 
2.6.31-17-generic #54-Ubuntu SMP x86_64 GNU/Linux 
openoffice.org-core 1:3.1.1-5ubuntu1 
OpenOffice.org 3.1.1 OOO310m19 (Build:9420)

---

### Post by mrsynock on 2010-03-22
same thing with two differents laptop under karmic up to date.

Did you find a bug report on launchpad ?

---

