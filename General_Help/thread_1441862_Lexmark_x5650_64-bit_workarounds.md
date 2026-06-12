---
title: "Lexmark x5650 64-bit workarounds"
date: 2010-03-29
forum: General Help
---

### Post by wbar2 on 2010-03-29
I am attempting to install a Lexmark x5650 on Ubuntu 9.10 64-bit. I download the drivers from here, and they install without error:
[http://www.downloaddelivery.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz]("http://www.downloaddelivery.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz")

However, when I print a test page I always get an error saying it cannot be processed. The computer definitely detects the printer (it even sees that my color ink is low). But, the printer can't process the documents for some reason.

The driver was written for 32-bit version, so maybe there is an issue with 64-bit? I saw in another post that there are workarounds (they just said search the forums), but I cannot find them anywhere. Anybody have any idea?

---

### Post by wbar2 on 2010-03-29
What's really interesting now is that after installing the drivers in Ubuntu, the printer will not work in Windows! It says its printing on the screen, but the display on the printer keeps saying "canceling..."

So something has been set inside the printer itself that is causing problems. I think if I reinstall the Windows drivers in Windows, it will then be able to at least print in Windows again. Not really sure what's going on...

---

### Post by wbar2 on 2010-03-30
Got it working!!!

I added libstdc++5 per the following instructions:
[http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000](http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000)

Then I ran the driver installation file that is found on the Lexmark page.
[http://www.downloaddelivery.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz](http://www.downloaddelivery.com/downloads/cpd/lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz)

During the installation it asks you to connect the USB. When I did Ubuntu was already adding a printer. So, when I finished that installation, I had two x5650's installed. The one that the installer created didn't work, but for some reason the one that Ubuntu created did!

I haven't tested scanning yet, but printing definitely works!:D

---

### Post by wbar2 on 2010-04-01
I'm unable to get scanning to work on 9.10. But, good news. It works on 10.04 beta1!

I installed the printer on a 32-bit version of 10.04 beta1. It still needed libstdc++5 in order to print properly (see above). After installing the printer I went to xSane Image Scanner and it was detected automatically. I didn't use that (I just wanted a simple test), but went back and used Simple Scan and it worked great!

---

### Post by irishrick on 2010-05-02
Any thoughts on whether or not this will work on the Lexmark x5495.  I'm just about ready to install 10.04 with hopes that the workaround will work

---

### Post by cparke on 2010-10-21
Hi, I just installed Ubuntu 10.10 (64-bit) and wanted to install the driver for my Lexmark Z2420 wireless printer and was having the same difficulties as you, RE: Lexmark's driver only supports 32-bit (and does not support wireless printing setup) and it installs but nothing will print.  

Thanks to this thread, as well as this one: [http://ubuntuforums.org/showthread.php?t=1442219](http://ubuntuforums.org/showthread.php?t=1442219) , and some of my own variation, I am now setup with wireless printing on Lexmark and 64-bit Ubuntu, except I cannot see printer ink levels in Ubuntu (does that work for anyone?).  Here I will detail my thoughts and some open questions...

(1) libstdc++5 can be installed correctly using Synaptic Package Manager, without the need to use dpkg on the command line and copy libraries between the /usr/lib and /usr/lib32.  In my 10.10 installation it was initially installed for 64-bit only I think.

(2) The Lexmark installer also is using dpkg --force-architecture for its installation and consequently seems to putting their 32-bit driver files in the wrong directory (/usr/lib).  Does anyone know if I should  move those to lib32 like was done in the Digital Enigma link? (or course we don't have 64-bit versions of them)

(3) Even after doing the libstdc++5 thing, I still couldn't seem to install the printer (wired or wireless) using Ubuntu's interface.  So, I used CUPS and the PPD file instead.  To do that, you navigate to [http://127.0.0.1:631/](http://127.0.0.1:631/) in the web browser and go through administration to add printer.  In my case, I was adding it as a wireless printer using AppSocket/HP JetDirect with its host address specified as socket://192.168.1.201:9100 and I didn't even try the wired USB because I don't want that.  Anyway, when it asked for printer manufacturer, instead of making a selection, I skipped to the PPD file option and pointed it to /usr/lexinkjet/08zero/etc/lxZ2400.ppd and it accepted that and the printer started working wirelessly for me!

Again, ink levels are the only thing missing now, not a big issue but does anyone know anything further I should try or fix?

Thanks everything for your help!  64-bit OS is excellent!
CP

---

