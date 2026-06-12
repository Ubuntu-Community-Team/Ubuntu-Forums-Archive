---
title: "i can not install my mfc-990cw printer"
date: 2010-02-05
forum: General Help
---

### Post by themadbusdriver on 2010-02-05
can somneone please help me? i have no idea how to make it install as i am a ex-windows person i just got ubuntu on my comp today

---

### Post by cariboo on 2010-02-06
Your printer doesn't show up in the [Openprinting Database]("http://www.openprinting.org/printer_list.cgi?make=Brother"). It may be too new. Have you tried plugging in the usb cable, then going to System->Administration->Printing, to see if the printer is auto detected?

You may have to contact Brother to see if there is a driver for your printer. Most Brother printers have been plug and play over the last few years.

---

### Post by Yogotiss on 2010-02-06
> **themadbusdriver said:**
> can somneone please help me? i have no idea how to make it install as i am a ex-windows person i just got ubuntu on my comp today

You may want to try updating first if it is newly installed. (**[COLOR="blue"]Accessories[/COLOR]**>>**[COLOR="SlateGray"][COLOR="Blue"]Terminal[/COLOR][/COLOR]**) and type "**sudo apt-get update**". Restart and then configure your printer. What version of Ubuntu are you using?

---

### Post by plucky on 2010-02-06
There are drivers and install instructions on the [Brother Website](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-990CW)

Good Luck

---

### Post by ahalin on 2011-08-03
These instructions are fairly generic and worked on 9.04, 9.10, 10.04, 10.10 and 11.04, as at August 2011:

If you haven't already, download the following files from Brother ([http://goo.gl/hYWWG](http://goo.gl/hYWWG))

[INDENT]mfc990cwlpr-1.1.2-2.i386.deb
mfc990cwcupswrapper-1.1.2-2.i386.deb
brscan-skey-0.2.1-3.i386.deb
brscan3-0.2.9-1.i386.deb [/INDENT]

and install with Ubuntu Software Centre [11.04] or gdebi Package Manager [10.XX] (they are in the right mouse click menu ["RCM"]).

Set the Job Options eg paper size and print a test page from under the Settings tab. If all is well, duplicate the printer (RCM) and set one as black and white, one for colour. Finally set one as default (RCM)

xsane scanner should pick up the printer if all has gone well. I am still working on the 11.04 scanner software!

If you are still having problems, download brmfc990cw.ppd (although you might have generated this from a previous install using more complex methods). 

For distros prior to 11.04, then go to >System >Administation >Printer and install new printer using the ppd file brmfc990cw.ppd. In 11.04, hit the "Super Key", type in print and open the Printing application, and select add new printer (plus sign top left)]

:)

---

