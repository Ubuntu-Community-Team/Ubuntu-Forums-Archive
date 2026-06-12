---
title: "TeighaFileConverter with Wine"
date: 2010-11-21
forum: General Help
---

### Post by kleinempfaenger on 2010-11-21
Hi,
I want to run the TeighaFileConverter in Wine, on Ubuntu 10.10. Installing no problem, but when I try to run it, I get the following error message:

"Runtime Error

R6034

An application has made an attempt to load the C runtime library incorrectly."

Where is the problem? Is it Wine, Ubuntu, or the TeighaFileConverter?
Do I have to install any other packages?

Ah, I want to use this program to convert AutoCAD .dwg to .dxf, as I work with QCad for some time now. Are there any improvements?

Greetings, kl

---

### Post by linux-pjotr on 2010-11-29
I am just guessing, have no clue.
But maybe install MS C-runtime libraries for wine via
 wintricks (wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks))
would help.
Just download, run 'sh winetricks' and select the proper MS-package to install.
Good luck!

---

