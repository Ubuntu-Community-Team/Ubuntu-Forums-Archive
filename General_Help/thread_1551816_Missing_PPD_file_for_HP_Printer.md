---
title: "Missing PPD file for HP Printer"
date: 2010-08-12
forum: General Help
---

### Post by Nomad Dome on 2010-08-12
I am running Ubuntu 10.04 and attempting to install an HP Photosmart C6200.

Using HP Device Manager- Setup, I am able to detect the printer,  I receive an error 

Found device: hp:/net/Photosmart_C6200_series?ip=192.168.1.2
-error: No PPD found for model photosmart_c6200_series using new algorithm. Trying old algorithm...
error: No PPD found for model photosmart_c6200 using old algorithm.
error: No appropriate print PPD file found for model photosmart_c6200_series

There is no matching ppd file here: usr/share/ppd/hplip/HP.  There are no PPD files for any photosmart printer.

---

### Post by Nomad Dome on 2010-08-12
Also, I've tried to add the printer via System/Administration/Printing

There is a message "not connected" and no discovered printers.

When I try to connect to the server, I get a CUPS server error "failed to connect to server".

---

### Post by earthpigg on 2010-08-12
im digging around for info on that printer.

while i dig, see it listed here? [http://localhost:631/admin](http://localhost:631/admin)

---

### Post by earthpigg on 2010-08-12
found [this]("http://www.openprinting.org/printer/HP/HP-PhotoSmart_C6200")

> HP PhotoSmart C6200

bla bla bla

Best output quality reachable with the HPLIP driver (***printer compatible to HP DeskJet 990C***), especially the 4800-dpi high resolution mode gives excellent photo quality.

bla bla bla

try using that ppd.

i saw a lot of chinese (?) language stuff on this printer. did you buy this in southeast asia or something crazy? companies have been known to call a single product by different names for different markets so they can sell for drastically different prices without anyone noticing.

---

### Post by earthpigg on 2010-08-12
also, the .tar.gz file [here]("http://sourceforge.net/projects/hplip/files/") is handy to have around. it has ppd files that ubuntu doesn't have, for whatever reason.

---

### Post by Nomad Dome on 2010-08-12
The printer is a c6280  (6200 series).   It is well supported on Ubuntu 10.04 according to the HPLIP site.  [http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c6200_series.html](http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c6200_series.html) 

According to that site, it is supported after HPLIP 2.7.9

I downloaded and installed 3.10.6.  

HP Linux Imaging and Printing System (ver. 3.10.6)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=net, timeout=5, ttl=4, search=(None) desc=0, method=mdns)
\warning: No PPD found for model photosmart_c6200_series using new algorithm. Trying old algorithm...
error: No PPD found for model photosmart_c6200 using old algorithm.
error: No appropriate print PPD file found for model photosmart_c6200_series

Issue 1:
I had problems with this printer in the past and tried many software things to fix it.  Ends up that it needed a new logic board- which I replaced today.  It works fine with my Mac.  I think I borked something in my Ubuntu when installing things from Synaptic.

NOTE: Firefox can't establish a connection to the server at localhost:631

Issue 2: 
Even though I may have screwed up some settings or have some conflict, I would think there should be a PPD file in the HP Set up.  There is none listed for any photosmart printer.

---

### Post by Nomad Dome on 2010-08-12
Solved it!

sudo apt-get remove --purge cups
sudo apt-get install cups

After reinstalling CUPS, then I was able to use System/Administration/Printing and add it from there.

---

### Post by Lex_x64 on 2010-08-14
Thanks Nomad; purging and reinstalling ended up working for me as well. 

I had already installed the extra ppd's but it kept complaining that I needed to restart the CUPS process and it couldn't finish installing the printer, in case anyone else has my specific issue.

---

### Post by fzn on 2012-06-03
> **Nomad Dome said:**
> Solved it!

sudo apt-get remove --purge cups
sudo apt-get install cups

After reinstalling CUPS, then I was able to use System/Administration/Printing and add it from there.

you re right !! thahanks very much:p

---

