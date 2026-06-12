---
title: "Prepress publications"
date: 2010-05-04
forum: General Help
---

### Post by dwel on 2010-05-04
I'm trying to rid my life completely of windblows, but. I can not find a program that will allow me to create publications and print to pdf with composite or separations of cmyk. 

So I discovered wine, which miraculously enough has allowed me to install publisher 2007, and yes it works =] I have also installed PrimoPDF. 

How do I get publisher to recognize that primo is install in .wine/drive_c ? Until I can get this figured out I will have to keep my copy of xp going. I can do all the work I need to but I have to reboot to be able to print.

Any suggestions?

Thx
Dwel

---

### Post by tgalati4 on 2010-05-04
Can't help you with windows (because I don't use it), but a quick search of cmyk:

apt-cache search cmyk

Have you tried scribus?

---

### Post by dwel on 2010-05-04
I appreciate the reply. Scribus can work sorta like it wants to try and do cmyk, but it doesnt. Plus it cant print separations. 

I think my question was more on the line of wine. how to get 1 wine program to see that another is installed. like adding a pdf printer to the fake windows environment. Cause I actually got the publisher program working, just doesnt recognize the printer.

---

### Post by tgalati4 on 2010-05-04
I'm thinking you need to set up a virtualized Windows environment.  You need to set up proper Windows print spoolers and I don't think you can do that in Wine.  (Wine is not an emulator--WINE) it simply provides dlls (dynamic link libaries) for Windows binaries to sort of function.  Running a print spooler so you can hang your virtual PDF printer requires an emulator.  And WINE.

There are tutorials for different ways to set up a Virtual Machine so you can load a complete copy of Windows, load your publishing apps, and finally load your printers then you should have the functionality that you require.

---

### Post by dwel on 2010-06-16
Wow, its been a while, sorry i didnt say thanks sooner. I started using vbox, and all is well.

Now if we could just get a native steam client.

---

