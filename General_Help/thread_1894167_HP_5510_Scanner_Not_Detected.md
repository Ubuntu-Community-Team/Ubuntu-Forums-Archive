---
title: "HP 5510 Scanner Not Detected"
date: 2011-12-11
forum: General Help
---

### Post by kinnerc on 2011-12-11
Hi Folks:

I'm a bit stumped right now. I'm running Ubuntu 11.10 64-bit and now have an HP Photosmart 5510. Everything is working except the scanner.

The printer is attached to my computer via the USB port. I have HPLip installed and the system had no problem detecting the printer, finding the driver and installing it. I put wireless on and my laptop also had no problem using this connection. I also just figured out that if an SD memory card is inserted into the printer it will auto-mount to the desktop. I didn't expect that.

Given all this I also didn't expect the problem I'm having. When I run SimpleScan it says there is no scanner detected. To the best of my knowledge and research, this is a SANE printer. Since it is attached via the USB port and even mounting memory cards on the printer via this USB port I have to believe that the USB cord is good.

I have downloaded and installed the latest hplip software 3.11.10. hp-check and it ran, but gave a couple of remarks that didn't make any sense to me:

==========================================================
---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
HP_Photosmart_5510_series
-------------------------
Type: Printer
Device URI: hp:/usb/Photosmart_5510_series?serial=CN18O081JY05NR
PPD: /etc/cups/ppd/HP_Photosmart_5510_series.ppd
PPD Description: HP Photosmart 5510 Series, hpcups 3.11.10
Printer status: printer HP_Photosmart_5510_series is idle.  enabled since Sun 11 Dec 2011 10:43:13 PM EST
error: Unsupported model: Photosmart_5510_series
error: Communication status: Failed

================================================

And yet, printing works fine. I even made sure I installed it with an hp: URL so that it depended on HPLIP in CUPS.

================================================
-----------------
| USB I/O SETUP |
-----------------

Checking for permissions of USB attached printers...

HP Device 0xa111 at 002:008: 
    Device URI: hp:/usb/Photosmart_5510_series?serial=CN18O081JY05NR
error: Unsupported model: Photosmart_5510_series
=================================================

Also:

=================================================
--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.
=================================================

How is it doing ANYTHING if it cannot discover the USB device (the printer)?

When I installed it, I was able to find the driver for it with no problem. And printing and memory card mounting works. 

Scanning does not.

running sane-find-scanner gives:

=================================================
found USB scanner (vendor=0x03f0 [HP], product=0xa111 [Photosmart 5510 series]) at libusb:002:008
=================================================

but...

=================================================

----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate).
========================================================

I'm stumped. Does anyone have any experience with the HP 5510 running under Ubuntu 11.10?
------
Doc Kinne
Somerville, MA

---

### Post by bdenize on 2012-01-02
Hi

I met the same issue.
I re launched the installation but manually (not automatic)...

The launcher did not find the instances for xsane and asked if I wanted it to download it.

Worked fine for me !

I used hplip-3.11.12 by the way.

Hope it helps.

---

### Post by crazy bird on 2012-01-02
> **bdenize said:**
> Hi
 
I met the same issue.
I re launched the installation but manually (not automatic)...
 
Best advise! Remove the old hplip driver (terminal: **sudo apt-get purge hplip**) and re-install the hplip driver manually. If HPLIP is missing any dependencies, it will ask you if HPLIP should install this automatically. This is the best way to do it. At the beginning you also get some questions whether HPLIP should install some functions like Jetdirect and Fax support, answer every question with Yes (**Y**).
 
At the end when the installation procedure is ready and it ask you if it should reboot the system or plugin the printer/scanner, choose rebooting the system. This works better. 
 
Keep in mind that during the installation procedure your pinter/scanner is turned off! After the reboot you can switch it on and Ubuntu/HPLIP will recognize is automatically.

---

### Post by cblanquer on 2012-01-04
Hi,

I bought this afternoon a HP 5510 and followed your recommendation on the installation on my main Ubuntu 11.10 box. 
Working like a charm, XSANE shows a great scan definition. Pretty satisfied and thanks for theinformation provided, it was not evident where to solve the "scaner not found" issue.
Regards.

---

### Post by Drowz0r on 2012-01-09
Printing works great but scanner not so much. I did a manual install after it wasn't working at all at first but now I just get this screenie.

Any ideas?

---

### Post by Drowz0r on 2012-01-11
> **Drowz0r said:**
> Printing works great but scanner not so much. I did a manual install after it wasn't working at all at first but now I just get this screenie.

Any ideas?

Actually, if you have this problem, set Right X and Right Y to max in advance options (CTRL + 6) and it should work then.

---

### Post by KP314 on 2012-01-14
This thread was helpful. I'm running Lubuntu and hp-setup would not detect the 5510 printer at all. The native printer utility detected it but recommended the 3300 series for the driver and I could not find the 5510 on the list of printers. I installed it with the 3300 series driver and the printer then worked but Simple Scan would not detect the scanner.  I tried the "sudo apt-get purge hplip" command as mentioned but the printer would still not get detected when I ran hp-setup. After reading this thread further and others and by looking in Synaptic, I figured out that I was on HPLIP version 3.11.7 which was too old for this printer. I downloaded and installed HPLIP version 3.11.12 and now it gets detected by hp-setup and after install Simple Scan works as well.

---

### Post by erikonthenet on 2012-01-26
Same here, did the purge, installed 3.11.12: one big success story! I used the wireless connection

---

### Post by bo.vestergaard on 2012-06-26
Thanks guys! I just got my 5510 wireless working in Ubuntu 11.04. Thank you for the suggestions :)

---

### Post by jjolds on 2012-11-16
I discovered that the printer does not work with windows 8!  HP has been no help.If you find out anything let me know!
> **kinnerc said:**
> Hi Folks:

I'm a bit stumped right now. I'm running Ubuntu 11.10 64-bit and now have an HP Photosmart 5510. Everything is working except the scanner.

The printer is attached to my computer via the USB port. I have HPLip installed and the system had no problem detecting the printer, finding the driver and installing it. I put wireless on and my laptop also had no problem using this connection. I also just figured out that if an SD memory card is inserted into the printer it will auto-mount to the desktop. I didn't expect that.

Given all this I also didn't expect the problem I'm having. When I run SimpleScan it says there is no scanner detected. To the best of my knowledge and research, this is a SANE printer. Since it is attached via the USB port and even mounting memory cards on the printer via this USB port I have to believe that the USB cord is good.

I have downloaded and installed the latest hplip software 3.11.10. hp-check and it ran, but gave a couple of remarks that didn't make any sense to me:

==========================================================
---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
HP_Photosmart_5510_series
-------------------------
Type: Printer
Device URI: hp:/usb/Photosmart_5510_series?serial=CN18O081JY05NR
PPD: /etc/cups/ppd/HP_Photosmart_5510_series.ppd
PPD Description: HP Photosmart 5510 Series, hpcups 3.11.10
Printer status: printer HP_Photosmart_5510_series is idle.  enabled since Sun 11 Dec 2011 10:43:13 PM EST
error: Unsupported model: Photosmart_5510_series
error: Communication status: Failed

================================================

And yet, printing works fine. I even made sure I installed it with an hp: URL so that it depended on HPLIP in CUPS.

================================================
-----------------
| USB I/O SETUP |
-----------------

Checking for permissions of USB attached printers...

HP Device 0xa111 at 002:008: 
    Device URI: hp:/usb/Photosmart_5510_series?serial=CN18O081JY05NR
error: Unsupported model: Photosmart_5510_series
=================================================

Also:

=================================================
--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.
=================================================

How is it doing ANYTHING if it cannot discover the USB device (the printer)?

When I installed it, I was able to find the driver for it with no problem. And printing and memory card mounting works. 

Scanning does not.

running sane-find-scanner gives:

=================================================
found USB scanner (vendor=0x03f0 [HP], product=0xa111 [Photosmart 5510 series]) at libusb:002:008
=================================================

but...

=================================================

----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate).
========================================================

I'm stumped. Does anyone have any experience with the HP 5510 running under Ubuntu 11.10?
------
Doc Kinne
Somerville, MA

---

