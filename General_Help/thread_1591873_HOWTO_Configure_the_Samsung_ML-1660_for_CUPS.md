---
title: "HOWTO: Configure the Samsung ML-1660 for CUPS"
date: 2010-10-10
forum: General Help
---

### Post by teejaybee on 2010-10-10
G'day,

I recently got a Samsung ML-1660 printer and while it worked fine with  the unified linux driver provided by Samsung, I didn't really like how  that driver did its business with regards to installing old static  libraries and other stuff that I don't need and most certainly don't want  going stale and causing problems down the track.

So I read up online on how to troubleshoot printer problems with CUPS and came to the following solution on my Ubuntu 10.04 machine:

1) Download the Samsung unified printer driver from their [website]("http://www.samsung.com/") (UnifiedLinuxDriver_*.tar.gz)
2) Extract /cdroot/Linux/noarch/at_opt/share/ppd/ML-1660spl.ppd to a temporary directory.
3) For 32 bit: extract /cdroot/Linux/i386/at_root/usr/lib/cups/filter/rastertosamsung* to a tmp dir
4) For 64 bit: extract /cdroot/Linux/x86_64/at_root/usr/lib64/cups/filter/rastertosamsung* to a tmp dir
5) sudo cp tmpdir/rastertosamsung* /usr/lib/cups/filters
6) sudo chmod 755 /usr/lib/cups/filters/rastertosamsung*
7) sudo chown root:root /usr/lib/cups/filters/rastertosamsung*
8) Plug the printer in - Ubuntu should recognise it connected via USB and give it its own name
9) Add a new printer with cups via System -> Administration ->  Printing. In the "Choose Driver" section select "Provide PPD file" and  browse and select ML-1660spl.ppd that you extracted earlier to a tmp  dir.
10) Print a test page, and away you go!

I hope this benefits someone.

Cheers.

---

### Post by hibou107 on 2010-11-01
Hi, I'm a newbe in Ubuntu and also have a ML 1660 printer, can you explain more in your tutorial?

For exemple, in the folder filters there is 4 files with the name started by rastertosamsung
So do I need to repeat 4 times the commands:
```
sudo chmod 755 /usr/lib/cups/filters/rastertosamsung
```with each file?


> **teejaybee said:**
> G'day,

I recently got a Samsung ML-1660 printer and while it worked fine with  the unified linux driver provided by Samsung, I didn't really like how  that driver did its business with regards to installing old static  libraries and other stuff that I don't need and most certainly don't want  going stale and causing problems down the track.

So I read up online on how to troubleshoot printer problems with CUPS and came to the following solution on my Ubuntu 10.04 machine:

1) Download the Samsung unified printer driver from their [website]("http://www.samsung.com/") (UnifiedLinuxDriver_*.tar.gz)
2) Extract /cdroot/Linux/noarch/at_opt/share/ppd/ML-1660spl.ppd to a temporary directory.
3) For 32 bit: extract /cdroot/Linux/i386/at_root/usr/lib/cups/filter/rastertosamsung* to a tmp dir
4) For 64 bit: extract /cdroot/Linux/x86_64/at_root/usr/lib64/cups/filter/rastertosamsung* to a tmp dir
5) sudo cp tmpdir/rastertosamsung* /usr/lib/cups/filters
6) sudo chmod 755 /usr/lib/cups/filters/rastertosamsung*
7) sudo chown root:root /usr/lib/cups/filters/rastertosamsung*
8) Plug the printer in - Ubuntu should recognise it connected via USB and give it its own name
9) Add a new printer with cups via System -> Administration ->  Printing. In the "Choose Driver" section select "Provide PPD file" and  browse and select ML-1660spl.ppd that you extracted earlier to a tmp  dir.
10) Print a test page, and away you go!

I hope this benefits someone.

Cheers.

---

### Post by hibou107 on 2010-11-01
OK, I've just tried, just need to select the right .ppd file from source and evrything's perfect!

---

### Post by miquelinho87 on 2010-11-16
Goodevening. I'm sorry for my not perfect english, but I hope that you will understand. I've red about the installation of the samsung ml-1660, and I tried to install it, but I could not. After 1 hour, and several attempts, I found the problem: at the point number 5) of the guide, the command isn't "sudo cp tmpdir/rastertosamsung* /usr/lib/cups/filters", but "sudo cp tmpdir/rastertosamsung* /usr/lib/cups/filter", without the final s in the word "filter".

These are the correct passages:
1) Download the Samsung unified printer driver from their [website]("http://www.samsung.com/") (UnifiedLinuxDriver_*.tar.gz)
2) Extract /cdroot/Linux/noarch/at_opt/share/ppd/ML-1660spl.ppd to a temporary directory (That could be the Desktop).
3) For 32 bit: extract /cdroot/Linux/i386/at_root/usr/lib/cups/filter/rastertosamsung* to a tmp dir
4) For 64 bit: extract /cdroot/Linux/x86_64/at_root/usr/lib64/cups/filter/rastertosamsung* to a tmp dir
5) sudo cp tmpdir/rastertosamsung* /usr/lib/cups/filter
6) sudo chmod 755 /usr/lib/cups/filter/rastertosamsung*
7) sudo chown root:root /usr/lib/cups/filter/rastertosamsung*
8) Plug the printer in - Ubuntu should recognise it connected via USB and give it its own name
9) Add a new printer with cups via System -> Administration ->   Printing. In the "Choose Driver" section select "Provide PPD file" and   browse and select ML-1660spl.ppd that you extracted earlier to a tmp   dir.
10) Print a test page, and away you go!

However I want to thank [teejaybee]("http://ubuntuforums.org/member.php?u=1041835") for the precious guide.__

---

### Post by pianomans on 2010-12-02
yes, it works... Thanks. I have ubuntu 10.10, and without 's' on 'filter'.

---

### Post by vasilbelarus on 2010-12-19
Is double-sided printing work fine?

---

### Post by christi99k on 2010-12-30
i can't print two sided. any suggestion pls.

---

### Post by henshu70 on 2011-03-07
Thanks a lot teejaybee for posting the guide and thanks also miquelinho87 for your corrections. My Samsung ML-1660 printer is now finally working. However, **[COLOR="Red"]without duplex options[/COLOR]**. Please, if anybody knows how to enable this, I would very much appreciate your help (and as one can see from the posts some other folks too). Although I suspect this is probably the driver feature which is not included.

Thanks

> **miquelinho87 said:**
> Goodevening. I'm sorry for my not perfect english, but I hope that you will understand. I've red about the installation of the samsung ml-1660, and I tried to install it, but I could not. After 1 hour, and several attempts, I found the problem: at the point number 5) of the guide, the command isn't "sudo cp tmpdir/rastertosamsung* /usr/lib/cups/filters", but "sudo cp tmpdir/rastertosamsung* /usr/lib/cups/filter", without the final s in the word "filter".

These are the correct passages:
1) Download the Samsung unified printer driver from their [website]("http://www.samsung.com/") (UnifiedLinuxDriver_*.tar.gz)
2) Extract /cdroot/Linux/noarch/at_opt/share/ppd/ML-1660spl.ppd to a temporary directory (That could be the Desktop).
3) For 32 bit: extract /cdroot/Linux/i386/at_root/usr/lib/cups/filter/rastertosamsung* to a tmp dir
4) For 64 bit: extract /cdroot/Linux/x86_64/at_root/usr/lib64/cups/filter/rastertosamsung* to a tmp dir
5) sudo cp tmpdir/rastertosamsung* /usr/lib/cups/filter
6) sudo chmod 755 /usr/lib/cups/filter/rastertosamsung*
7) sudo chown root:root /usr/lib/cups/filter/rastertosamsung*
8) Plug the printer in - Ubuntu should recognise it connected via USB and give it its own name
9) Add a new printer with cups via System -> Administration ->   Printing. In the "Choose Driver" section select "Provide PPD file" and   browse and select ML-1660spl.ppd that you extracted earlier to a tmp   dir.
10) Print a test page, and away you go!

However I want to thank [teejaybee]("http://ubuntuforums.org/member.php?u=1041835") for the precious guide.__

---

### Post by Phil1581 on 2011-03-30
Thanks, but I had to add under 'Printer Properties','Job Options' 'Tray' 'automatic', otherwise no paper loaded.
Also I found that letting Ubuntu automatically find the driver also required the above addition.

---

### Post by Corsari on 2011-04-10
I've tested the steps by my own 'cause I have one of those printers network shared by a windoz pc

If you connect to it and provide the ppd only, a warning pops about the raster filters

So I removed the first test (the printer installs), I've added the ***rastertosamsung**** filters in ***/usr/lib/cups/filter/*** and I've repeated the add printer from samba network: it works.

Now I'm able to print from ubuntu to a windoz pc sharing on ml-1660 printer.

Thank you for this guide.

---

### Post by spyroskaftanis on 2011-05-03
> **miquelinho87 said:**
> Goodevening. I'm sorry for my not perfect english, but I hope that you will understand. I've red about the installation of the samsung ml-1660, and I tried to install it, but I could not. After 1 hour, and several attempts, I found the problem: at the point number 5) of the guide, the command isn't "sudo cp tmpdir/rastertosamsung* /usr/lib/cups/filters", but "sudo cp tmpdir/rastertosamsung* /usr/lib/cups/filter", without the final s in the word "filter".

These are the correct passages:
1) Download the Samsung unified printer driver from their [website]("http://www.samsung.com/") (UnifiedLinuxDriver_*.tar.gz)
2) Extract /cdroot/Linux/noarch/at_opt/share/ppd/ML-1660spl.ppd to a temporary directory (That could be the Desktop).
3) For 32 bit: extract /cdroot/Linux/i386/at_root/usr/lib/cups/filter/rastertosamsung* to a tmp dir
4) For 64 bit: extract /cdroot/Linux/x86_64/at_root/usr/lib64/cups/filter/rastertosamsung* to a tmp dir
5) sudo cp tmpdir/rastertosamsung* /usr/lib/cups/filter
6) sudo chmod 755 /usr/lib/cups/filter/rastertosamsung*
7) sudo chown root:root /usr/lib/cups/filter/rastertosamsung*
8) Plug the printer in - Ubuntu should recognise it connected via USB and give it its own name
9) Add a new printer with cups via System -> Administration ->   Printing. In the "Choose Driver" section select "Provide PPD file" and   browse and select ML-1660spl.ppd that you extracted earlier to a tmp   dir.
10) Print a test page, and away you go!

However I want to thank [teejaybee]("http://ubuntuforums.org/member.php?u=1041835") for the precious guide.

You are a god my friend!!
I haven't any problem in Fedora 13 and Ubuntu 10.04, but I had in Fedora 15.
Printer (ML 1665) doesn't work! I follow your guide and all are good now!!
Thanks!!!!!!! :D:D:D

---

### Post by RickyMcRick on 2011-06-03
Great post. Was looking around for a while until I found this - install worked perfectly following the updated steps. Strange that the Ubuntu auto-install came up with printer models on either side of this one (e.g. ML-1651 and model numbers higher than ML-1660) but not this printer. I sent a nonsensical email to Samsung saying they should provide better support for Ubuntu in response :)

---

### Post by michaelam on 2011-10-18
Super job, got it working right away...thanks a lot for the information.

---

### Post by black.door67 on 2012-05-03
Double sided Printing can be enabled by editing /etc/cups/ppd/ML-16*.ppd file 

add this lines file at the end then u will find option in the properties Duplex Printing

*% =========================================================
*%  Duplex Printing
*% =========================================================
*% =========================================================
*%  Printer Features
*% =========================================================

*OpenUI *Duplex/Double-sided Printing:  PickOne
*OrderDependency: 60 AnySetup *Duplex
*DefaultDuplex: None
*Duplex None/None: " <</Duplex false>> setpagedevice"
*Duplex DuplexNoTumble/Long Edge: "
    <</Duplex true /Tumble false>> setpagedevice"
*End
*Duplex DuplexTumble/Short Edge: "
    <</Duplex true /Tumble true>> setpagedevice"
*End
*?Duplex: "
   save
      currentpagedevice /Duplex get
        {currentpagedevice /Tumble get
            {(DuplexTumble)}{(DuplexNoTumble)}ifelse
         }{(None)} ifelse = flush
   restore
"
*End
*CloseUI: *Duplex

---

### Post by Bas Roufs on 2012-05-04
[I][QUOTE=teejaybee;9946145]
1) Download the Samsung unified printer driver from their [website]("http://www.samsung.com/") (UnifiedLinuxDriver_*.tar.gz)
2) Extract /cdroot/Linux/noarch/at_opt/share/ppd/ML-1660spl.ppd to a temporary directory.
3) For 32 bit: extract /cdroot/Linux/i386/at_root/usr/lib/cups/filter/rastertosamsung* to a tmp dir
4) For 64 bit: extract /cdroot/Linux/x86_64/at_root/usr/lib64/cups/filter/rastertosamsung* to a tmp dir
5) sudo cp tmpdir/rastertosamsung* /usr/lib/cups/filters
6) sudo chmod 755 /usr/lib/cups/filters/rastertosamsung*
7) sudo chown root:root /usr/lib/cups/filters/rastertosamsung*
8) Plug the printer in - Ubuntu should recognise it connected via USB and give it its own name
9) Add a new printer with cups via System -> Administration ->  Printing. In the "Choose Driver" section select "Provide PPD file" and  browse and select ML-1660spl.ppd that you extracted earlier to a tmp  dir.
10) Print a test page, and away you go!

[I]Hello Everybody,
When working with Kubuntu 11.04 and a few preceding versions, I have been able to print perfectly well with Samsung ML-1660 - along the lines of the instructions at this page. However, in Kubuntu 11.10 and 12.04, the printer is not being recognised any more - even after exactly carrying out the instructions here, *Ubuntu simply does not detect the printer. There must be some bug, because in a few preceding versions the printer detection worked flawlessly. At some forum, I saw the recommendation to install again some old Linux kernel - however, this caused various other complications. That's why,I hope to get ideas for other remedies or "workarounds" for this problem. 

Thanks, respectfully yours, Bas Roufs.[/I]

---

### Post by Bas Roufs on 2012-05-05
Today, the problems seems to be solved for "80%". The system, Kubuntu 12.04, again recognises the printer. I do manage to print test pages. I also do manage to print from other applications - however, I often need to switch on and off the printer in order to get a page printed.

Respectfully yours,
Bas Roufs.

---

### Post by Bas Roufs on 2012-09-21
Hello Everybody,
during a few years I managed to work well with my ML-1660 printer along the lines of these instructions:

> **miquelinho87 said:**
> Goodevening. I'm sorry for my not perfect english, but I hope that you will understand. I've red about the installation of the samsung ml-1660, and I tried to install it, but I could not. After 1 hour, and several attempts, I found the problem: at the point number 5) of the guide, the command isn't "sudo cp tmpdir/rastertosamsung* /usr/lib/cups/filters", but "sudo cp tmpdir/rastertosamsung* /usr/lib/cups/filter", without the final s in the word "filter".

These are the correct passages:
1) Download the Samsung unified printer driver from their [website]("http://www.samsung.com/") (UnifiedLinuxDriver_*.tar.gz)
2) Extract /cdroot/Linux/noarch/at_opt/share/ppd/ML-1660spl.ppd to a temporary directory (That could be the Desktop).
3) For 32 bit: extract /cdroot/Linux/i386/at_root/usr/lib/cups/filter/rastertosamsung* to a tmp dir
4) For 64 bit: extract /cdroot/Linux/x86_64/at_root/usr/lib64/cups/filter/rastertosamsung* to a tmp dir
5) sudo cp tmpdir/rastertosamsung* /usr/lib/cups/filter
6) sudo chmod 755 /usr/lib/cups/filter/rastertosamsung*
7) sudo chown root:root /usr/lib/cups/filter/rastertosamsung*
8) Plug the printer in - Ubuntu should recognise it connected via USB and give it its own name
9) Add a new printer with cups via System -> Administration ->   Printing. In the "Choose Driver" section select "Provide PPD file" and   browse and select ML-1660spl.ppd that you extracted earlier to a tmp   dir.
10) Print a test page, and away you go!

However I want to thank [teejaybee]("http://ubuntuforums.org/member.php?u=1041835") for the precious guide.__

However, ever since a few months, I get stuck at step 8. In other words: *Ubuntu does not auto-recognise any more this printer. At present I work with Kubuntu 12.04, along with KDE 4.9.1. 

Does anybody have a clue how to fix this problem? Thanks, respectfully yours,
Bas Roufs.

---

### Post by jhoo on 2013-01-29
fwiw, followed the instructions using a Samsung ML-1665 on Lubuntu 12.10, worked perfectly.  many thanks!

---

### Post by Baur87 on 2013-04-27
Since this is still the first hit of many search engines when looking for a Linux driver for Samsung printers: For many Samsung and Xerox printers (including the Samsung ML-1660) there is a free driver available. It is called [SpliX]("http://splix.ap2c.org/") and is available in the Ubuntu repositories as “printer-driver-splix”.

---

### Post by mescobal on 2013-05-16
Tanks a lot!! Fixed the issue in Lubuntu 13.04.

Marcelo.

---

