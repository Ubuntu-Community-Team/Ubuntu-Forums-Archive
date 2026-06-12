---
title: "This code appear when I print a page, strange."
date: 2012-07-04
forum: General Help
---

### Post by EgaRana on 2012-07-04
Hi, I have some problem with printer device. It is Ricoh MP C3001.
When I use Windows, it's going normal to print a file or an image.
But, Ubuntu give me a problem. When I'm going to print an image, the print out from the printer was a lot of blank pages and some of them have a code like this :

> %!PS-Adobe-3.0 %% %% mark () () (201207042334) {setuserinfo} stopped cleartomark %%

Can someone help me?

---

### Post by msammels on 2012-07-04
Are you printing a PostScript file? Or have you installed a PostScript driver?

---

### Post by EgaRana on 2012-07-04
I have installed this driver and it's doesn't affect.
Here is the URL :
[http://www.openprinting.org/printer/Ricoh/Ricoh-Aficio_MP_C3001]("http://www.openprinting.org/printer/Ricoh/Ricoh-Aficio_MP_C3001")

---

### Post by prshah on 2012-07-04
> **EgaRana said:**
> It is Ricoh MP C3001.
the print out from the printer was a lot of blank pages and some of them have a code

This happens if you are using a driver that is different from your printer. For example, in this case, you may be using the Postscript driver instead of the PCL (Printer Control Language) driver (or vice versa).

Try changing the driver from CUPS (Common Unix Printing System). 


CUPS is installed by default. To access cups (for settings, admin, etc) open a browser, and enter the below in the ADDRESS bar```
http://localhost:631
```

You can also use [http://127.0.0.1:631](http://127.0.0.1:631) .

If you are asked for a username and password in CUPS (Eg, when performing admin tasks), use your username and password.

Please post back with more details if you need more assistance.

---

