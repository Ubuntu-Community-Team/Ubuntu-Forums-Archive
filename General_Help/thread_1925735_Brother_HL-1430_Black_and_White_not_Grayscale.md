---
title: "Brother HL-1430: Black and White not Grayscale"
date: 2012-02-15
forum: General Help
---

### Post by duncan12 on 2012-02-15
Hi everyone.

I have a Brother HL-1430-series which still works very well. It is a grayscale printer, and is connected over USB.

However when I print a document involving colour, it comes up in black and white (ie lots of little dots), instead of grayscale (ie a shade of grey).

That's if I print from the Ubuntu box, however if I print from a networked computer, it works fine and prints in grayscale, even though - you would think - the driver etc. happens on the computer it's plugged into, not the computer that sent the print request.

I'm not the best macro photographer, but here's two proof-of-concept photos.

[http://www.box.com/s/svamd500z0msd1aciqy8](http://www.box.com/s/svamd500z0msd1aciqy8) (over network from XP)
[http://www.box.com/s/fgeabznggtja2ff7obd1](http://www.box.com/s/fgeabznggtja2ff7obd1) (directly over USB)

It all automatically installed when I plugged the USB cable into my Acer Aspire 5534 - a notification popped up saying "installed and ready to print". I've tried manual installs too to no avail.

Thanks.

---

### Post by plucky on 2012-02-15
I don't have your printer,but I would suggest you open the CUPS interface and see what is the default color/greyscale set for your printer.

To get to the CUPS interface,type into the address bar of Firefox ```
http:127.0.0.1:631/
``` and then navigate to your printer and display the "default options" and see what is set.

Good Luck

---

### Post by duncan12 on 2012-02-15
> **plucky said:**
> I don't have your printer,but I would suggest you open the CUPS interface and see what is the default color/greyscale set for your printer.

To get to the CUPS interface,type into the address bar of Firefox ```
http:127.0.0.1:631/
``` and then navigate to your printer and display the "default options" and see what is set.

Good Luck

Hi,
I did not realise that page was there :p

Anyway, when I go to the Printer Options for that printer there is no option regarding colour. When I click "General" I get 
> Page Size: A4	
Economy Mode: Off
Media Source: Automatic
Resolution: 300x300 DPI

JCL: > Media Type: Plain Paper
Banners: > Starting Banner: none
Ending Banner: none
Policies:> 
Error Policy: retry-job
Operation Policy: default 

So nothing to do with colour modes :confused:. I may have looked in the wrong place, but that's all the settings I could find.

Thanks for your reply

---

### Post by plucky on 2012-02-16
Sorry,As I don't have your printer so I cannot advise any further,but that is where I can change my Brother Inkjet printer.

Maybe it doesn't have the option as it is a Black & White Laser printer.

Good Luck

---

### Post by duncan12 on 2012-02-16
Ok, thanks anyway.

There must be a way somehow, as printing over the network gives the desired grayscale, whereas it's just printing directly from the Linux box gives black and white dots.

Therefore it somehow seems to do with the way Linux/Ubuntu handles the file it sends for printing instead of the driver itself...

---

### Post by duncan12 on 2012-02-18
Does anybody else have the Brother HL-1430 series?

If you can just tell me if you do or don't have the same problem that would be a start.

Thanks

---

### Post by demonipuch on 2012-02-19
Have you tried with drivers provided on Brother website?

---

### Post by kurt18947 on 2012-02-19
> **demonipuch said:**
> Have you tried with drivers provided on Brother website?

Like here: 
```
 http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-1430

```  Be sure to read the "before you install" part.  There is .rpm & .deb stuff mixed together and some commands don't apply to newer Ubuntu distros but it's still worth a read.  If that doesn't work, you might be able to use a generic printer language e.g. pcl 5 rather than a Brother driver.  Brother's lasers seem to mirror HP laser printers.  For example, my MFC-7820N is sometimes identified as an HP-4050 when running "find networked printer".  Another possibility would be to look at the Brother laser drivers in the repositories.  My MFC-7820N works better with the CUPS driver from the repositories than it does with with default Brscript3, for instance.

---

### Post by duncan12 on 2012-02-21
I downloaded the .deb from the website you gave, thanks.

```
duncan@Duncan-Linux:~$ sudo dpkg -i ./Downloads/cupswrapperHL1430-1.0.2-1.i386.deb
[sudo] password for duncan: 
Selecting previously deselected package cupswrapperhl1430.
(Reading database ... 358349 files and directories currently installed.)
Unpacking cupswrapperhl1430 (from .../cupswrapperHL1430-1.0.2-1.i386.deb) ...
Setting up cupswrapperhl1430 (1.0.2-1) ...
ERROR : Brother LPD filter is not installed.
rm -f /usr/lib/cups/filter/brlpdwrapperHL1430
chmod: cannot access `/usr/local/Brother/inf/brHL1430rc': No such file or directory
chmod: cannot access `/usr/local/Brother/inf': No such file or directory
cups stop/waiting
cups start/running, process 26857
```

Upon installing this, a new printer appears in my list, simply named "HL1430". When printing a document, in the Print Preview, my old printer installation shows the black and white dots, whereas the new printer that appears shows grayscale. Yay!

However I then found that the newly installed printer doesn't print. The old one still does. I've tried matching the usb:// URL on both, but this doesn't help. I've tried making a new printer, with the right URL but the new driver (which appears in the list), but documents still don't print.

Any more ideas?

Thanks,
Duncan

---

### Post by demonipuch on 2012-02-21
> ERROR : Brother LPD filter is not installed.You need to install the LPD driver first and then install the cupswrapper driver.

ps : If you find it difficult to install your printer, i've written a script to make it easy. There is a thread here : [http://ubuntuforums.org/showthread.php?t=1898181](http://ubuntuforums.org/showthread.php?t=1898181)

---

### Post by kurt18947 on 2012-02-21
demonipuch is correct, LPD then CUPS.  I wonder if you'll need to uninstall the old misbehaving printer as well, not certain.

---

### Post by duncan12 on 2012-02-23
Thanks everyone.

Here's what I did:

```
duncan@Duncan-Linux:~$ sudo apt-get remove cupswrapperhl1430
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cupswrapperhl1430
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
After this operation, 94.2 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 358355 files and directories currently installed.)
Removing cupswrapperhl1430 ...
cups stop/waiting
cups start/running, process 6303
----------------------------------------------------------------------- 17:43:46
duncan@Duncan-Linux:~$ dpkg -i '/home/duncan/Downloads/hl1430lpr-1.1.2-1.i386 (1).deb'
dpkg: error: requested operation requires superuser privilege
----------------------------------------------------------------------- 17:43:53
duncan@Duncan-Linux:~$ sudo dpkg -i '/home/duncan/Downloads/hl1430lpr-1.1.2-1.i386 (1).deb'
Selecting previously deselected package hl1430lpr.
(Reading database ... 358349 files and directories currently installed.)
Unpacking hl1430lpr (from .../hl1430lpr-1.1.2-1.i386 (1).deb) ...
Setting up hl1430lpr (1.1.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/HL1430': No such file or directory
chown: cannot access `/var/spool/lpd/HL1430': No such file or directory
chgrp: cannot access `/var/spool/lpd/HL1430': No such file or directory
chmod: cannot access `/var/spool/lpd/HL1430': No such file or directory
start: Unknown job: lpd
dpkg: error processing hl1430lpr (--install):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 hl1430lpr
----------------------------------------------------------------------- 17:44:01
duncan@Duncan-Linux:~$ sudo dpkg -i '/home/duncan/Downloads/cupswrapperHL1430-1.0.2-1.i386 (1).deb'
Selecting previously deselected package cupswrapperhl1430.
(Reading database ... 358361 files and directories currently installed.)
Unpacking cupswrapperhl1430 (from .../cupswrapperHL1430-1.0.2-1.i386 (1).deb) ...
Setting up cupswrapperhl1430 (1.0.2-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperHL1430
cups stop/waiting
cups start/running, process 6398

```

There were errors with the first one, however the CUPSwrapper one installed successfully, suggesting a change.

I then deleted both installed printers from the "Printing" program. I connected the USB plug and got a notification - "Configuring new printer", "Printer successfully installed".

I printed a basic test document in LibreOffice, to no avail (prints but still with black and white dots).

I then went into the properties of the newly installed printer and changed the driver from "Brother HL1430" to "Brother HL1430 for CUPS".

Upon printing the same document (simply 'GREEN' in bold and green) I get what looks like a grayscale print! Looking at it very closely still shows dots, however this is probably due to the printer's oldness.

Also worth noting is in the print preview it shows a colour preview. This means that the computer is sending the printer the right document, unlike before when it was sending the printer black and white dots.

All good and fixed.

Thanks everyone for the help! :p

---

### Post by kurt18947 on 2012-02-24
What resolution is the printer capable of and what are you using?  An easy way to check if you're using Firefox is to start to print a document, select the HL-1430 then click on the 'image quality' tab. Some printer/drivers are capable of 600 d.p.i. or more but default to 300 d.p.i.

---

### Post by duncan12 on 2012-02-26
> **kurt18947 said:**
> What resolution is the printer capable of and what are you using?  An easy way to check if you're using Firefox is to start to print a document, select the HL-1430 then click on the 'image quality' tab. Some printer/drivers are capable of 600 d.p.i. or more but default to 300 d.p.i.

Thanks, it was already set to 600dpi.

Looking now you can't see any dots from 10 cm away - that was me scanning for the error at the time and looking close up :)

---

