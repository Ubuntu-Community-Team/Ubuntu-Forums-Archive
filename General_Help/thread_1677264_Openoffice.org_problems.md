---
title: "Openoffice.org problems"
date: 2011-01-28
forum: General Help
---

### Post by kavizi on 2011-01-28
I'm having sporadic issues with the openoffice.org program.  Sometimes, power point presentations will crash the program and then I can't open any open office programs without rebooting the computer.  The problem seems to be just with powerpoint files and I'm not sure what the issue could be.  Any suggestions?

---

### Post by PrivateSNAFU on 2011-01-28
Have you tried installing libreoffice, seems a lot better.  

[http://www.omgubuntu.co.uk/2011/01/new-ppa-makes-installing-libreoffice-on-ubuntu-easy/](http://www.omgubuntu.co.uk/2011/01/new-ppa-makes-installing-libreoffice-on-ubuntu-easy/)

OpenOffice seems to have stagnation for a while before being forked into libreoffice.  Fingers crossed this works.

---

### Post by Hagar Delest on 2011-01-28
You can also try the vanilla version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68) NB: it can run in parallel with LibO.

Remember that the .ppt import/export filters have been reverse engineered since there was no specification available. So no wonder there are some problems with certain files.

---

### Post by kavizi on 2011-02-03
I installed the 'LibreOffice' without difficulty, but I'm still having the same problems as with openoffice.  The 'vanilla' version sounds a bit complex and risky for me.  I'm not so good with messing around with programming.  Is there anything else that can be done?  Can I save the power point under a different format?

---

### Post by vanadium on 2011-02-03
I rarely have crashes nowadays with the Ooo that came with Ubuntu, and currently with LibreOffice (fingers crossed).

But indeed, it is a very good idea to save the files to the odp format, quite the program and load the odp version to continue working. When finished, you can still "export" to ppt if there is a need.

It is much preferred, and a good habit, to work with the native file formats of the program. This is the only format that supports all the features of your application, and will guarantee maximum stability. Just "import" and "export" foreign formats as the need arises.

---

### Post by kavizi on 2011-02-06
Would you recommend trying to install the vanilla version despite my lack of experience?  Or should I just carry on trying to save things in ODP format?

---

### Post by Hagar Delest on 2011-02-06
Basically, better use the vanilla version IMHO (better quality checks, but it may change with LibO if many users switch from OOo to LibO).

And the most important is to use ODF instead of closed formats like .ppt. ODF insures that your data doesn't rely on a single company. ODF is supported by other applications.

---

### Post by khelben1979 on 2011-02-06
Maybe you're looking for [odf-converter-integrator]("http://katana.oooninja.com/w/odf-converter-integrator") to solve your issue with PowerPoint files?

---

