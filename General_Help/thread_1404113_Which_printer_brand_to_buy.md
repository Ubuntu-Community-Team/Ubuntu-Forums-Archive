---
title: "Which printer brand to buy?"
date: 2010-02-11
forum: General Help
---

### Post by chipppy on 2010-02-11
Good Evening people

I am looking at buying a new printer.  After the hell to get the old Brother going I would like some thoughts on the following.

Which brand of printer/scanner combo has the best driver support for Linux.  I do like to support (buy) those that support us with good driver support?

Please not I dont what to start a brand flame wars I just would like to here peoples thoughts about driver support by brands.

Cheers
chipppy

---

### Post by darolu on 2010-02-11
Here you'll find a list, all major brands are included.

[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters)

Any "renowned" brand printer should do it, if you want to be safe, don't buy the latest super-fancy-full-of-options printer, as full support for it may not be available. I have had HP printers and they always get the job done (I still use an old laserjet 1100).

---

### Post by OrangeCrate on 2010-02-11
If you search the forums, you'll find the brand that is recommended most is HP. Personally, I have an Officejet J4550 All-in-One, and it has worked fine through several releases.

---

### Post by tubbygweilo on 2010-02-11
Chippy, may I suggest you investigate the [openprinting database]("http://www.openprinting.org/printer_list.cgi") as I used this site to research the driver required by my [Brother-HL-2140]("http://www.openprinting.org/show_printer.cgi?recnum=Brother-HL-2140") & [thread]("http://ubuntuforums.org/showthread.php?t=987865&highlight=2140+printer").

---

### Post by kg4cna on 2010-02-11
I'll add my vote for HP printers. They're well supported.

---

### Post by Nunu on 2010-02-11
+ 1 for HP... I won't suggest lexmark though

---

### Post by chipppy on 2010-02-13
Good Evening

HP it is then,  Thanks heaps peopls.  The openprinting site is great.  Pity I didnt find that one while trying to get my old Brother going.

Cheers
chipppy

---

### Post by efflandt on 2010-02-13
Any printer that does HP PCL (which is backwards compatible) or Postscript should be easy.

Many years ago my HP LaserJet 4L worked with printcap configured as hplj3 for lpr/lpd before there was an hplj4l driver.  And WordPerfect 5.1 for DOS worked with its LaserJet III driver for an HP 2200dtn (fonts were excellent, but graphics were 300 dpi instead of 1200 dpi).

And when I needed to print something from my laptop to a Kinko's printer (now FedEx Office) Xerox printers were not listed in the Linux version I was running, so I just used generic level 2 postscript, and it worked.

I currently have a Lexmark C543dn (which does HP PCL and Postscript) and from Ubuntu install CD it worked with older Lexmark color laser driver.  Lexmark's install script does not seem to work for Ubuntu, but Lexmark does have ppd files, and if you point Printing configuration to the unzipped ppd directory, it works fine with cups (including duplex).

---

### Post by LiudasLT on 2010-02-19
Hello everyone,

At home I have Canon Pixma MP610.
This printer works perfeclty in ubuntu 9.10:
Automaticaly detect and printer and scaner drivers.

But with Canon Pixma iP2500 and Canon LPB-810 I still haveing problems (hope will solve soon, because its not on my PC and I dont have much attempts).

P.S. I am interested too what manfacturers provides most Open Source software friendly solutions :)

---

### Post by joeknoodle on 2010-02-19
+1 for HP C4880. Get the HP LIP from repos for ink levels and other functions.

---

### Post by hwttdz on 2010-02-19
I'll vote for brother, OS agnostic is better than OS compatible.  Also I don't think it makes much sense to have a printer connected to an individual machine, I think it makes more sense to hook it to the network and let anything use it and not have to worry about "is that computer on?".

---

