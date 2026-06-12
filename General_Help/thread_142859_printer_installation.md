---
title: "printer installation"
date: 2006-03-11
forum: General Help
---

### Post by GolfGeek on 2006-03-11
I've just installed ubuntu and like much of it but getting frustrated at a few points. I went to install a printer (Lexmarl E232) which the system recognized but in proceding, I selected Lexmark but there is no driver per se for the E232. I tried the E but certain areas overlap in printing. Step 2 was to go to the Lexmark site, select the printer and select the debian/gnu version (ubuntu was not there) and click to download and it says it has downloaded "print-drivers-linux-glibc2-x86.deb" . What the hell do I do now? I've figured out how to get to terminal mode but what do I run or where do I do it.  I'm getting frustrated because I can't find a guide that says this is how you install programs, add hardware, what these commands do and what their equivilent is in windows. I'm sure this is a common dilemma for newbies.

---

### Post by rejser on 2006-03-11
you can always check [http://ubuntuguide.org/](http://ubuntuguide.org/)
go to the directory where you downloaded print-drivers......
type 
sudo dpkg -i print-drivers.... to install the package

---

### Post by GolfGeek on 2006-03-11
Thanks for the reply. I'll try that. Incidently, how do you use quick reply. I see the box but nothing is active. I can't type in it. Is there a secret key?? Also, you said to go to the directory where I downloaded the drivers. Where do I find that? Foxfire ran the download to the desktop but I still haven't figured out the topology here.

---

### Post by Den-Can on 2007-04-20
Here some help for Lexmark E232 laser printer user...In the printer installation ( printer selection panel ) simply put HP Laserjet ( Just Laserjet .. no model number ) .. Works great here ...

---

### Post by Sef on 2007-04-20
Check out [LinuxPrinting]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-E232").  Says it works perfectly.

Lexmark is not very Linux friendly.  HP and Epson are [GNU/Linux friendly printers]("http://www.linux-foundation.org/en/OpenPrinting/Database/SuggestedPrinters").

> I'm getting frustrated because I can't find a guide that says this is how you install programs, add hardware, what these commands do and what their equivilent is in windows.

Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

Also read Psychocat&#347; [installing software]("http://www.psychocats.net/ubuntu/installingsoftware").

---

