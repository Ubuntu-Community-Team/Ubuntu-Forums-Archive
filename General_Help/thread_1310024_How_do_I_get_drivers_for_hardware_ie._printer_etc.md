---
title: "How do I get drivers for hardware ie. printer etc"
date: 2009-11-01
forum: General Help
---

### Post by Asguard on 2009-11-01
:o Hi firstly  would like to say I am new to this type of OS have used XP and Apple and have noticed similarities to Apple layout.

I have installed the Ubuntu OS and everything is fine I do not seem to have any problems just yet. Taking me a while to get used to. 

I thought this was linux that's how unsure I am of this OS. I would like to know how do I get my scanner, printer etc to work on this OS as the sites support linux but not this. One supported ubuntu but ubuntu could not open the drivers. Did try to double click it did open but would not install so therefore wrong driver I assume.

So simple question where does everyone else get there drivers from for their printer etc.

Thanks

Asguard :(

---

### Post by hal8000 on 2009-11-01
Printing on linux/unix is done with a system called CUPS (Common Unix Printing System). Its already installed by default on Ubuntu, so system, admin printing will get you there.

A search on google for "ubuntu printer setup" revealed this site:

[http://nixcraft.com/getting-started-tutorials/468-howto-ubuntu-linux-setting-up-my-your-printer.html](http://nixcraft.com/getting-started-tutorials/468-howto-ubuntu-linux-setting-up-my-your-printer.html)

which gives you step by step instructions.

Scanning is a little more tricky, its done by software called "Sane", but
you need tp serach on google or next post remember to include at least your scanner make/model.
You can try a search on the forums as well, someone may have the same hardware, hope that helps.

---

### Post by hal8000 on 2009-11-01
On ubuntu and linux in general, theres a system called cups:

[http://nixcraft.com/getting-started-tutorials/468-howto-ubuntu-linux-setting-up-my-your-printer.html](http://nixcraft.com/getting-started-tutorials/468-howto-ubuntu-linux-setting-up-my-your-printer.html)


You need to quote make/model for your scanner, or search through the forums or google.

---

### Post by P4man on 2009-11-01
> **Asguard said:**
> 

I thought this was linux that's how unsure I am of this OS. I would like to know how do I get my scanner, printer etc to work on this OS as the sites support linux but not this. 

In linux, typically you get lucky and you dont need to install any drivers whatsoever. Its all right there by default. Well, typically might be a stretch, but for most things you dont need extra drivers.

For instance, printers. just go system > administration > printing. If your printer isnt listed there yet, click new and see if it finds it. You may have to confirm the brand and type and it will load the drivers for you. If you are unlucky, you have one of the guestimated 1% printers not in there and you might need to download a driver somewhere, in which case just post the type of printer here.

For scanners its similar.  Go to Applications > Graphics > Xsane. If your scanner is supported it will be listed and you can start scanning right away. If its not in there, you might be in trouble :) But again post brand and type.
> 
One supported ubuntu but ubuntu could not open the drivers. Did try to double click it did open but would not install so therefore wrong driver I assume.

So simple question where does everyone else get there drivers from for their printer etc.

Generally speaking in ubuntu (and most linux distor's) either your hardware is supported and using/installing it is so easy people think they have to take an extra step. Or the hardware is not supported out of the box, in which case the options range from challenging to virtually impossible to get it working. Its very rarely a driver can be installed through a double click though.

---

### Post by Asguard on 2009-11-02
Hi thank you everyone will get back on this in the next few days. May not have time today as away till Friday but will post later. Much appreciated.

---

### Post by Asguard on 2009-11-07
Hi back now. Got the drivers ok thankyou. I find the printer setup very unfriendly though. Done a test page it only comes out in two colours havent a clue what it all means as it does not print black cyan only in red and yellow. Find this very strange. Will print something and see later and report back if a problem.

---

### Post by Asguard on 2009-11-08
I find Ubuntu not very user friendly in setting things up. My printer has been recognised now but will only print in red and yellow. Do not understand the set up unnecessarily difficult. How do I get it to print black and other colours? I guess I am just not used to this system yet but so far not over impressed.

XSane Scanner comes up but cannot see how to find my scanner click on help says file not found. How do I get it to find my scanner please? Epson Perfection V350 PHOTO

---

### Post by P4man on 2009-11-08
You need a driver for that particular scanner. You can get it here:
[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

select your distro (ubuntu) and fill out the rest. Then grab the .DEB package (either 32 or 64 bit depending which ubuntu you got)
Save it, double click it

As for the printer, what printer is it?

---

### Post by Asguard on 2009-11-09
Hi thanks for the info but the scanner drivers will not unload says Error: Dependency is not satisfiable

Printer is Canon IP4600. I am using 64 bit Ubuntu

---

### Post by P4man on 2009-11-10
> **Asguard said:**
> Hi thanks for the info but the scanner drivers will not unload says Error: Dependency is not satisfiable


you're downloading the wrong package no doubt. Since I assume you have ubuntu 9.10 or 9.04 you need this one:
DEB 64bit package [libltdl7] (**for Ubuntu 8.10 or later**)

> Printer is Canon IP4600. I am using 64 bit Ubuntu

You can download a driver from canon's website here:
[http://software.canon-europe.com/products/0010649.asp](http://software.canon-europe.com/products/0010649.asp)

Again you need the debian (.deb) package. When you download it you will get an archive with 2 .deb packages inside, you have to install them both. Looks like Canon doesnt provide a 64 bit driver but you can force the use of the 32 bit driver and it appears to work fine according this this thread:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=975747](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=975747) 

Which also explains how to force the install through a terminal.

---

### Post by Asguard on 2009-11-11
Hi been to site downloaded the files makes no difference they will not unload. 

I can see why no one has linux now as if it is this difficult to get drivers who wants to mess about trying to get them. Not impressed with this ubuntu at all now. Was at first but not now. 

Any other ideas please.

---

### Post by Asguard on 2009-11-11
Hi well some how I have managed to get scanner going but still have problems with the printerPrinter works but will only print in red and yellow looked at settings and they are set to RGB color should it be on another setting CMY color or CMYK or KCMY.

Thanks for your help I am getting there slowly tho lol. Sorry for my rant earlier message but I do find the os unfriendly and it uses strange things like drawer etc I think it is going to take ages to get used to. I do like tho that the speed of this os is very fast. 

Anyway please can someone help as to what setting my printer should be on so it uses black ink and other colours. Thank you:mad:

---

### Post by ramjet_1953 on 2009-11-11
This link may be of use to you:

[http://www.openprinting.org/show_printer.cgi?recnum=Canon-iP4600](http://www.openprinting.org/show_printer.cgi?recnum=Canon-iP4600)

Regards,
Roger :D

---

### Post by Asguard on 2009-11-14
Hi tried this and still no joy as to printing all colours and pictures properly. Prints words ok but not pictures. misses a lot of the pictures as does not know colours. Not sure what to do here. Any help for printer Canon IP4600

---

