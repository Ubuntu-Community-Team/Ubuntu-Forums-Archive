---
title: "Printing Problems *PLEASE HELP*"
date: 2010-01-09
forum: General Help
---

### Post by AVDa on 2010-01-09
I updated to the recent 9.10 version of Ubuntu and found that my printer no longer works.  When trying to print, the printer just blinks and *occasionally* makes a noise and prints out a partial line of text or whatever.

It's a USB connecting HP Deskjet D1420 that is not a network printer and does not need to be networked.

lsusb returns:
Bus 006 Device 002: ID 147e:1000 Upek 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 03f0:7904 Hewlett-Packard 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

So... the printer is detected.  That's probably a good thing, right?

Even in my printers menu, the option to add a printer is greyed out...

When trying to connect to a network in the printers menu, I get: " There was an error during the CUPS operation: 'httpConnectionEncrypt failed'. "

I'm pretty lost about what I need to do on this one.  Usually, I can figure things out...

Any takers?  I need what help I can get.

Thanks!

---

### Post by lyall on 2010-01-09
I would first remove the printer form your Printer configuration list and restall it.

If it does not work see the follow link for some info
[http://www.openprinting.org/show_printer.cgi?recnum=HP-DeskJet_D1420]("http://www.openprinting.org/show_printer.cgi?recnum=HP-DeskJet_D1420")

good luck and fun have learning

---

### Post by AVDa on 2010-01-11
Now it says that cups can't start and that I can't connect to the admin server.  This is really starting to become a problem.  How did ubuntu print in the previous version?  It did just fine without the hpconfig utility and all the other additional steps...  What happened?  Does anyone know?

---

### Post by JC Cheloven on 2010-01-11
Try using hplip from terminal. For example 
```
hp-setup -u
```
will run hp-setup with a gui environment. Check the manpages to find out more: ```
info hp-setup
```

---

### Post by AVDa on 2010-01-11
I'll let you know how it turns out.

---

### Post by AVDa on 2010-01-11
Searching... (bus=usb, search=(None), desc=0)
/error: No PPD found for model deskjet_d1400_series using new algorithm. Trying old algorithm...
error: No PPD found for model deskjet_d1400 using old algorithm.
error: No appropriate print PPD file found for model deskjet_d1400_series
error:  Printer queue setup failed.  Please restart CUPS and try again.

Close, but no cigar.  See, this happens even after I search in multiple locations and select the provided ppd files.  My printer worked in the last version of Ubuntu.... It's fun and interesting to sift through this stuff, but I need my printer to work in under 48 hours.  Even worse was the day that I found out my printer wouldn't work... I had a final to turn in and was down to the wire.  Needless to say, it was turned in late.   Nearly a month later and bleh....

---

### Post by AVDa on 2010-01-12
Isn't there a way to print without using CUPS?  If I could never use it again, that would be perfect.

Moved to here: [http://ubuntuforums.org/showthread.php?p=8656196#post8656196](http://ubuntuforums.org/showthread.php?p=8656196#post8656196)

(started a new thread, really)

---

