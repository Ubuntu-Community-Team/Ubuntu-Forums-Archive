---
title: "Installing Epson Stylus Office BX535WD printer"
date: 2012-02-03
forum: General Help
---

### Post by PiHalbe on 2012-02-03
Hey everyone,

I have bought an Epson Stylus Office BX535WD printer after making sure that drivers for printing and scanning exist. I want to use it via network (wifi, which should not make a difference, I guess).

Scanning works fine with Simple Scan after installing the iScan utilities. *thumbsup*

However, the included *epson-escpr* package does not include the printer driver for the model. Only its predeccessor is supported. Using that driver, however, does not yield nice results (colors are not aligned, among other things).

So I installed the ESC-P-R package *epson-inkjet-printer-escpr_1.1.1-1lsb3.2_amd64.deb *from the [EPSON website]("http://download.ebz.epson.net/dsc/search/01/search/searchModule")* (where you can also get the iscan stuff). This makes the printer nicely available in the selection. And when adding it by selecting the network printer, it is automagically recognized.

Still, **I cannot get it to print with this driver**. It would just make silly noises and **drain the ink level** and not be able to abort the job. Shutting down helps, after which I have to reinsert the ink cartridges to make him continue.

Also, two-sided print is offered neither in the nice Ubuntu print menu nor the extended settings (where I can select but not apply this setting).

I **did**, however, manage to print pages via using the BX600FW ubuntu standard driver (not via BX525WD, its predeccessor, which will yield the same problems). Of course, this is only one-sided and the printer margins are a little off. Still, it's the best I could manage so far.

Is there any chance, anybody got a BX535WD to run flawlessly (or at least farily) under Ubuntu? If so, please let me know, I would really appreciate that or any other hints on how to get this printer to work properly. :)

Thanks and cheers,
Achim

* Before, I took it from the [Avasys website]("http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/"), which is no longer responsible for Epson Linux drivers.

---

### Post by enbeto on 2012-05-11
Hi there,

what a pity to hear this, it seems a nice printer.
Did you manage to make it work properly? And what about the duplex function?
I was thinking on buying one of these, but if it can't work under ubuntu I will then look for another one.
Thanks in advance!

---

### Post by PiHalbe on 2012-05-12
Just briefly:


[LIST]
[*]The printer works with BX600FW drivers using 3rd-party cartridges (which do not provide a counter chip, fortunately).
[*]Duplex printing does not work., unfortunately.
[*]New 12.04 automatically detects this printer as BX535WD, but this breaks the printing process. I manually use BX600FW instead.
[*]Scanning works fine.
[/LIST]
I am using it via WiFi, I don't know if USB support is better.

---

### Post by enbeto on 2012-05-14
Ok, thanks for the reply!

---

### Post by enbeto on 2012-07-04
Hi again,

I finally bought one of these printers.
The driver from epsilon allowed me to use duplex printing, also in network. After installing it, the printer BX535wd appears in the cups list, I selected and it just worked.

However, I haven't been able to use the scanner through the network (using usb is working fine).
Maybe I haven't properly installed the iscan utilities and missed something... Did you do anything special?
Thanks!

---

### Post by enbeto on 2012-07-05
Hi!
I finally managed to make it work. Now I'm happily duplex-printing and scanning, all over the network.
For the printing I just installed the proper epson driver:
[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/)
For the scanning, after installing the packages iscan-data, iscan-core and the network plugin from here:
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)
I had to add the line
net printer_ip_address 1865
in the file /etc/sane.d/epkowa.conf, where printer_ip_address is the ip address of the printer and 1865 is the port to be used.
Hence, for my case, I had to fix the ip address for the printer.

Best!

---

### Post by PiHalbe on 2012-07-05
Concerning the scanning via wireless, I did not do anything special. I just closely followed the instructions on their website. I remember installing a total of three packages for this. I do not use iScan for scanning but Simple Scan which works fine (but gets some hickups, once in a while).

Cool that the wireless printing works for you in all its glory. I shall try reinstalling the printer to get things working. By epsilon drivers you mean Epson drivers?

EDIT: Thanks for the information. I'll see if this fixes things for me.

---

### Post by enbeto on 2012-07-05
Hi!

It seems that our replies just crossed.
Thanks for your answer. Strange that in my case, without editing the epkowa.conf file, it did not work at all. Now simple scan, xsane and iscan all work. I'm in 10.04 so that could maybe make the difference.
Jeje! Yes, by epsilon driver I didn't mean an arbitrarily small driver... I got it from here
[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/)

Best!

---

### Post by robenroute on 2012-11-22
Just in case someone stumbles across this thread: I posted something on the Mint forums (that should work with Ubuntu as well): [Installing BX535WD]("http://forums.linuxmint.com/viewtopic.php?f=42&t=115637")

Bought the BX535WD, installed it, and it works flawlessly, including wireless scanning!

---

### Post by meyhub on 2013-06-05
Software, unplug the the printer if connected by USB. Reinstall the drivers but download the newer Epson Driver dated 25 March 09 from here [click here]("http://www.driversepson.com/epson-stylus-office-bx535wd-driver/")


It could be a bad install or comunication with the printer. You didn't say which windows you have ?


Cartridges even though they can be new can dry up a little or total if left redundant not printing in a printer. Lexmark are the worst for this, especially the older Lexmarks anyway.


You could call Epson for free telephone support and they would diagnose it over the phone to tell you if it is a fault with your printer.

---

