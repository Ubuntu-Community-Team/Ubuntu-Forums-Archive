---
title: "Artisteer 3 + ubuntu 11.04?"
date: 2011-06-07
forum: General Help
---

### Post by valero on 2011-06-07
(Translated with Google Translate) Hello. Recently I installed Ubuntu 11.04 and I know that with the installation of Artisteer is the problem. I was wondering if anyone know how to configure Wine ... that this program could work ... I specifically wanted to launch version 3 Thank you.

---

### Post by valero on 2011-06-07
I will be very grateful if it could somehow start to make it work.

---

### Post by valero on 2011-06-07
anyone know?

---

### Post by riodstar on 2011-10-07
Hi Valero, you must look that:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=22513](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22513)


Good luck

---

### Post by acc61287 on 2011-11-19
> **valero said:**
> (Translated with Google Translate) Hello. Recently I installed Ubuntu 11.04 and I know that with the installation of Artisteer is the problem. I was wondering if anyone know how to configure Wine ... that this program could work ... I specifically wanted to launch version 3 Thank you.

Try this:
Note: wine must install in your system

1. Download winetricks scripts
   wget [http://winetricks.org/winetricks](http://winetricks.org/winetricks)
2. Next type the following:
   sh winetricks corefonts tahoma fontfix d3dx9 vcrun6 ie6
   sh winetricks dotnet20
   sh winetricks gdiplus
if you encounter a problem in installing ie6 follow this steps:
(I assume that you have apache in your system)
1. Download ie6 manually
   [http://www.oldversion.com/download-Internet-Explorer-6.0.html](http://www.oldversion.com/download-Internet-Explorer-6.0.html)
2. Edit the winetricks script
   gedit winetricks
3. Comment line 7652 by putting #, just like this
   #w_download [http://download.oldapps.com/Internet_Explorer/ie60.exe](http://download.oldapps.com/Internet_Explorer/ie60.exe) 8e483db28ff01a7cabd39147ab6c59753ea1f533

   then add
w_download [http://127.0.0.1/download/msie60.exe](http://127.0.0.1/download/msie60.exe) 8e483db28ff01a7cabd39147ab6c59753ea1f533
   
   then save
4. Make folder download
   sudo mkdir /var/www/download
   sudo cp (Directory where msie6.exe reside) /var/www/download/msie6.exe
5. cd ~/.cache/winetricks/ie6" directory and make sure to rename the msie60.exe to ie60.exe
6. Type in the terminal
   sh winetricks ie6

I found the solution in this website
[http://code.google.com/p/winetricks/issues/detail?id=118](http://code.google.com/p/winetricks/issues/detail?id=118)

---

