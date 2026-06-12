---
title: "Printing to Fuji Xerox C5570?"
date: 2011-03-17
forum: General Help
---

### Post by AussieGuy on 2011-03-17
My work has just removed our nice easy HP Postscript printers, and replaced them with Fuji Xerox ApeosPort-IV C5570 machines.  All very nice, I'm sure, except that Fuji Xerox doesn't support linux - their web site provides printer drivers for Windows & Mac only.

Does anybody know how I can print to these printers - is there a third-party driver which will work?

Thanks,
-A.

---

### Post by JC Cheloven on 2011-03-17
Hi, in [this place]("http://www.openprinting.org/printers") you'll find the list of supported printers, avaliable drivers, etc, for linux.

Unfortunately, only a couple of models from fuji-xerox do appear, and yours isn't among them :(

I don't even see your printer listed in the fuji-xerox site itself:
[http://www.fujixeroxprinters.com.au/en/Support/Downloads.aspx](http://www.fujixeroxprinters.com.au/en/Support/Downloads.aspx)
... and only the same couple of printers are offered linux drivers by tha manufacturer, though. 

But perhaps [this link]("http://forums.linuxmint.com/viewtopic.php?f=51&t=57456") may be of help. It references [this site]("http://www.fujixerox.co.jp/download/apeosport/download/c4300series/linux/") in which your printer do appear, somehow in the linux section (unfortunately I don't understand chinesse). 
So it seems there may be a linux driver for you after all.

---

### Post by mulllhausen on 2011-10-05
the package found on the [http://www.fujixerox.co.jp/download/apeosport/download/c4300series/linux/](http://www.fujixerox.co.jp/download/apeosport/download/c4300series/linux/) does indeed work :) i just downloaded it from this page (actually i translated the page with google to figure out what the hell was going on there!) - the link is right at the bottom and appears to be a single package for all of the above fujixerox models.

i'm running ubuntu 11.04 and my printer is the fuji xerox docucenter-iv c3371. only the c3370 was on the list on that website but this still gets the job done (at least its all working fine so far...)

the link gives you a .rpm file, so convert this to .deb using alien:

sudo apt-get install alien dpkg-dev debhelper build-essential #install alien
sudo alien fxlinuxprint-1.0.3-2.i386.rpm #convert the package file
sudo dpkg -i fxlinuxprint_1.0.3-3_i386.deb #install the package on your machine

then navigate to the driver and unzip it:

cd /usr/share/cups/model/FujiXerox
sudo gunzip fxlinuxprint.ppd.gz

then open the printer settings up (system > administration > printing) and click the button to change the printer model. select the 'provide ppd file' radio button and select the file located at /usr/share/cups/model/FujiXerox/fxlinuxprint.ppd.

print a test page and all should work fine :guitar:

---

### Post by AussieGuy on 2011-10-05
Thanks for that.  However, the problem is not the printer driver, but the authentication.  The printers have been set up to be authenticated for each user by the Microsoft AD system used at my workplace, and there doesn't seem to any way for linux to supply that identification to the printer.

Thanks anyway!

-A.

---

