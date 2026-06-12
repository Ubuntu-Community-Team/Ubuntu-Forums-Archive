---
title: "HP Printer installation"
date: 2009-12-13
forum: General Help
---

### Post by n4pgw on 2009-12-13
I searched the forums for information on installing the HP PhotoSmart C6280 Scanner/printer/copier I own.  I did not find anything quickly in the forums easily so I went to HP.com.  HP directed me to the following link: > [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) which provided sufficient information to install the printer driver.  

I received a rather pleasant surprise.  It took less than two minutes to install and it worked first time.  What makes this amazing is that HP's Windows drivers for this printer are a PITA!  Over the last two years I have literally over a hundred hours trying to keep that printer and its drivers working in Windows XP and Vista.  

Leave it to the open source community to produce a quality product HP was incapable of producing.  This install worked just as easily on four different Ubuntu installations.  

I am posting this in case it is needed by others.

Thank you to all of you in the Open Source community for all your help for all others.

Buck

---

### Post by hansdown on 2009-12-13
Glad you got it working n4pgw.

---

### Post by miniyak on 2009-12-13
haha, yah.. ubuntu's ease with printers also surprised me at first

---

### Post by Dave67 on 2009-12-13
I think I should tell you that the HPlip software is written by HP for Linux this is one of the nice things about HP.

I have never had issues with drivers in ubuntu or have problems with the same printers on windows I have a HP c3150 all in one that works fine in windows 7 I just had to download and update the drivers needed for the printer. 


here is a link below you can go to for supported printers in Linux for the future printer you may buy.

[http://www.openprinting.org/printer_list.cgi](http://www.openprinting.org/printer_list.cgi)

just select the printer brand and model click show this will tell you if it will work in any Linux system and what version of the HPlip  you might need.

dave

---

### Post by Leppie on 2009-12-13
You had to install the hplip drivers? I just plugged in my hp printer and it worked... thought that the hplip driver was a standard include in ubuntu (or at least karmic)...

---

### Post by miniyak on 2009-12-13
yah maybe you did take too many steps.. 

system> administration> printing> add new printer should be all that it takes

makes setting up a printer on a windows machine seem like a headache... i've actually done em' side by side... 3minutes vs. 20mins, ubuntu ftw

---

### Post by Mski35 on 2009-12-13
I have the HP Photosmart C4250 All in one and printing was detected as soon as it was plugged in.  However I've tried scanning a photo in and it doesn't seem to recognize that it's connected to an OS.  Any ideas?

---

### Post by miniyak on 2009-12-13
im pretty sure i have the same model printer. lol

to scan it is pretty simple too, once you know how

go to applications> graphics> xsane image scanner

select your printer then you should be good to go, just press scan within xsane

---

### Post by n4pgw on 2009-12-14
> **miniyak said:**
> im pretty sure i have the same model printer. lol

to scan it is pretty simple too, once you know how

go to applications> graphics> xsane image scanner

select your printer then you should be good to go, just press scan within xsane

"select"?  It found and selected it on its own...

Thank you.  

My printer is on network and not connected to a computer.  

Thanks to you all.

Buck

---

### Post by Leppie on 2009-12-14
Through System>Administration>Printing it's also possible to add networked printers. Another place to manage printers is the cups administration page, you can find it by going to the following address in your web browser: [http://localhost:631](http://localhost:631)
On this page you can also change default settings for your printers at driver level.

---

### Post by elqusy90 on 2010-05-15
you are great

---

### Post by randumnumber on 2011-01-13
While the newer versions of ubuntu do detect printers, I have found that using the hplip tools supplied by HP allow you to use the printers tools easier, such as being able to press the scan button on the hp printer and having it auto-magically pop up on your computer. Also, the tools allow you to view ink cartage levels among other things that are not standard with the auto detect.

---

