---
title: "Defult Printer needs to 'print' to PDF file"
date: 2011-03-18
forum: General Help
---

### Post by brian242r on 2011-03-18
Hey, my dad just switched to 10.10 from windows 7 and we anyway. He away alot and takes his roster with him which the company supplies him through a windows program. The program works flawlessly under wine (with only one glitch) but when printing through the program, like on windows, you hit print and it sends it straight to the printer which works fine.

However, we need it to print to a PDF file so he can place it on his smart phone.

Any ideas how to set a default printer which saves to a file location instead of printing?

---

### Post by kostkon on 2011-03-18
Yes, install the package
```
cups-pdf
```
and you'll be able to print to a pdf file even from windows (under wine) apps (i.e. it will add a pdf printer to your system).

The pdf files are saved in a folder named *PDF* in your home folder.

Hope that helps.

---

### Post by brian242r on 2011-03-18
Yep that works! thanks for your help.:)

---

