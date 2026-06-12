---
title: "Brother DCP115C wont print"
date: 2009-11-01
forum: General Help
---

### Post by Mick1d on 2009-11-01
I managed to get this printer working in Jaunty but not in Karmic.  When I try to unpackage the drivers downloaded from the Brother Solutions centre it simply says incorrect architecture i386. Have used Ubuntu quite happily for 6 months but its so frustrating when you lose your printer on an upgrade.  Anybody help?  Afraid as a newbie I need detailed instructions to follow.

---

### Post by amano on 2009-11-01
**Brother DCP-115C printer part in Karmic:**

1) Turn off your printer

2) Open Synaptic

3) Search for the package brother-lpr-drivers-extra and install it and all its dependencies (the dependencies will be installed automatically, don't worry)

4) Turn on the printer

5) The printing wizard comes up

6) It doesn't find your printer automatically 

7) Look for the manual printer list in the wizard and open the brother section there

8) Choose the MFC-210C printer (yes, even for the DCP-115C)

9) Done.


**Brother DCP-115C scanner part in Karmic:**
1) For the scanner functionality download the brscan2 deb package from the brother homepage (choose the right one, eg the 32bit one for a 32 bit Ubuntu, the 64bit one for a 64 bit Ubuntu). Install it.

2) Now you need permissions. For Karmic create the file 55-libsane.rules in the folder /etc/udev/rules.d/   > sudo gedit /etc/udev/rules.d/55-libsane.rules

An insert this stuff into the file: > # USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"

Don't forget to save your file.

3) Then restart the computer (or at least restart udev) > restart udev

4) Open the Xsane program (available in the standard Ubuntu menus) and see if it finds your scanner now.

Report back if that worked. Otherwise you will have to add some additional rules.

---

### Post by amano on 2009-11-02
Mick, did it work?

---

### Post by algeroth29 on 2010-03-29
Hi,

I'm respond, this rules not works for scanning.

Xsane not found the scanner.

Cheers !

Algeroth29

---

### Post by amano on 2010-04-11
algeroth29: What is your printer/scanner model?

What is your Ubuntu version? Lucid or Karmic?

---

### Post by arluijen on 2010-08-20
For Ubuntu 10.04 this doesn't work: wizard quickly pops up after turning the printer on and then mentions it is unmounted. No further wizard after that.

System-Admin-Printing doesn't allow adding a new printer.

Any help ?

---

### Post by pienene on 2011-04-25
It actually worked for me  - but only the printer part. scanner is not working still. on 10.10

---

### Post by plucky on 2011-04-25
> **pienene said:**
> It actually worked for me  - but only the printer part. scanner is not working still. on 10.10

Go [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html) and download the scanner driver .deb file for your scanner and install.

Installation instructions are also provided on the same site.

Good Luck

---

### Post by pienene on 2011-04-25
I have installed it. and also added the rules. 
also tried to add the rule for user from Brother:
Ubuntu 9.10, 10.04 
1. Open "/lib/udev/rules.d/40-libsane.rules" file.
2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):

 The lines to be added--------------------------- 

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
 
3. Restart the OS. 

still can't get it working :confused:

---

### Post by pienene on 2011-04-25
still can't get it working :confused:[/QUOTE]

this is what I get
~$ dpkg -l | grep Brother
ii  brother-cups-wrapper-common               1.0.0-10-0ubuntu5                                 Common files for Brother cups wrapper packages
ii  brscan                                    0.2.4                                             Brother CUPS Printer Definitions

I am new to ubuntu, so I'm not sure about anything, but this means it is installed?

---

### Post by plucky on 2011-04-25
> **pienene said:**
> still can't get it working :confused:

this is what I get
~$ dpkg -l | grep Brother
ii  brother-cups-wrapper-common               1.0.0-10-0ubuntu5                                 Common files for Brother cups wrapper packages
ii  brscan                                    0.2.4                                             Brother CUPS Printer Definitions

I am new to ubuntu, so I'm not sure about anything, but this means it is installed?

If your printer is the DCP-115C,to which this thread relates,you have to install the brscan2 driver,not the brscan driver.

Good Luck

---

### Post by pienene on 2011-04-25
Thanks so much, Plucky! It's always something silly like that - I did note that brscan2 is what I need - but still ended up with the wrong one and couldn't spot it!!! 
Now everything works, really, thank you!
:KS

---

### Post by plucky on 2011-04-25
Well Done,Enjoy

---

