---
title: "Xsane and SCSI Epson Scanner not recognized except using sudo xsane"
date: 2009-11-25
forum: General Help
---

### Post by bdalzell on 2009-11-25
My Epson SCSI scanner has worked fine in my dual boot Ubuntu/AMIthlon (Amiga emulator) system for the last several years. When I upgraded from Intrepid to Jaunty a few weeks ago it stopped being available to Xsane.

It still runs from the Amiga/AMIthlon boot.
 
Trying to run Xsane from Applications>Graphics>Xsane gets me a "no devices available" error.

However :

~$> sudo sane-find-scanner
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

found SCSI processor "EPSON Perfection636 1.14" at /dev/sg5
  # Your SCSI scanner was detected. It may or may not be supported by SANE. Try
  # scanimage -L and read the backend's manpage.

sudo scanimage -L
device `epson2:/dev/sg5' is a Epson Perfection636 flatbed scanner
device `epson:/dev/sg5' is a Epson Perfection636 flatbed scanner
device `epkowa:scsi:/dev/sg5' is a Epson Perfection636 flatbed scanner

and running 

sudo xsane 

from a command line and ignoring the dire warnings that running Xsane as root may damage something results in the launching of Xsane and a successful scan, once I choose one of the three ways the system seems to be able to view the scanner.

Neither  "sane-find-scanner" nor "scanimage -L" find the scanner if I run them as the normal logged in user.

So how do I get Xsane to run the scanner as a normal application for a logged in user rather than as sudo?

---

### Post by bdalzell on 2009-12-03
The Solution to Xsane "Scanner Not Found" error after Ubuntu Hardy to Intrepid Ugrade 

I have a SCSI Epson Perfection636 flat bed scanner. I already had Xsane installed before I upgraded using the upgrade tool from System>Administration>Update Manager.
 
This was not a simple solution. In fact I probably devoted at least one full work day to learning how to fix this.

The first thing I tried - which did not work - was to use synaptic to completely remove Xsane and then to reinstall it.

I would not have been able to fixed Xsane without the help of Jon Labadie and a number of other helpful people on the Novalug mailing list. This solution is compiled from their instructions and suggestions and I am putting it all in one document to help others.

First here are a number of command line tools that may or may not be present on your Ubuntu system. They can be added using apt-get. They are lsscsi, scanimage.

If they are not present and you try to invoke them with sudo from the command line, then your system will instruct you as to how to get them via apt-get.

To list the SCSI devices (Linux includes your IDE and USB devices in its list of SCSI devices) if you have an real SCSI devices:

>lsscsi

Resulted in:

[5:0:0:0]    disk    ATA      WDC WD2500AAJB-0 01.0  /dev/sda
[5:0:1:0]    cd/dvd  IOMEGA   DVDRW4216IND-A   1.21  /dev/sr0
[6:0:0:0]    disk    ATA      WDC WD5000AAKB-0 05.0  /dev/sdb
[6:0:1:0]    disk    ATA      WDC WD800BB-22JH 05.0  /dev/sdc
[7:0:4:0]    process EPSON    Perfection636    1.14  -       
[8:0:0:0]    disk    ST325082 3A                     /dev/sdd
[9:0:0:0]    disk    Memorex  TD 2C            1.00  /dev/sde
[10:0:0:0]   cd/dvd  TSSTcorp CD/DVDW SH-W162L LC00  /dev/sr1

So the system did know about my scanner.

So I tried:

> sudo xsane

That, after dire warnings about not using Xsane as root, Xsane would find my scanner and run. Of course all the scans were saved as belonging to root and I had to do a sudo chmod on them, which was annoying.


Then - after a suggestion from Jon Labadie I tried this:

> sudo scanimage -L

Which told me what device had the scanner mounted on it even though I could only access it from my root account.
Here were my results:

device `epson2:/dev/sg6' is a Epson Perfection636 flatbed scanner
device `epson:/dev/sg6' is a Epson Perfection636 flatbed scanner
device `epkowa:scsi:/dev/sg6' is a Epson Perfection636 flatbed scanner

So now I know what device the scanner is being mounted on, in fact it is mounted on 3 devices. 

At that time in the process I was not sure what to do but found a suggestion at the Ubuntu Discussion Groups about trying to mount it from the command line:

> sudo chgrp scanner /dev/sg6
> sudo chmod 660 /dev/sg6n

This worked, allowing me as user to run Xsane, but I had to do it after each reboot.

As a temporary fix I wrote a little shell script to do it.

However I still would like to change the permissions for the scanner device to be for me the user rather than root.

Jon LaBadie told me about /etc/udev/rules and to create a file called:

/etc/udev/rules.d/45-scsi-scanner.rules

so I did:

sudo gedit /etc/udev/rules.d/45-scsi-scanner.rules

and then to add these lines to the file:

# permissions for EPSON Perfection636 SCSI Scanner.
SUBSYSTEM=="scsi_generic",ATTRS{vendor}=="EPSON",ATTRS{model}=="Perfection636",
NAME="%k", SYMLINK="scanner%n", MODE="0660", GROUP="scanner"


Jon notes important matters in association to creating and using the udev rule:

<quote>
If anyone tries to use the udev rule, they will have to customize it for their scanner.  In this case, the lsscsi and scanimage -l commands outputs have important info as each report what the device reports itself as.  

In this case, vendor EPSON and model Perfection636.  

These are both used in any udev rule you customize and the SPELLING/CAPITALIZATION/WHITESPACE are critical!
</quote>

Now that  I have created the scanner specific udev rule, Xsane runs fine from Applications>Graphics>Xsane under my user account. 

_________________________________

Postscript:

I do not know why the system finds three different instances of the scanner mounted but that is what happened as a result of running:

> sudo scanimage -L.

So  I did a directory listing for /etc/sane.d/

ls /etc/sane.d/

I found that among the many files in the subdirectory with the same file creation date, there was a file with a name: 

epkowa.conf.dpkg-old 

dated much more recently than all the other files in the subdirectory

When I looked in it

less /etc/sane.d/epkowa.conf.dpkg-old

The first lines looked like this:
<quote>
# epkowa.conf -- sample configuration for the EPKOWA SANE backend
# Copyright (C) 2004, 2008, 2009  Olaf Meeuwissen
#
# See sane-epkowa(5), sane-usb(5) and sane-scsi(5) for details.

# Detect all devices supported by the backend.
# If you don't have a SCSI device, you can comment out the "scsi"
# keyword.  Similarly for the other keywords.
#
usb
scsi
scsi EPSON    Perfection636
</quote>

While the first lines of the active file:

less /etc/sane.d/epkowa.conf looked like this:

<quote>
# epkowa.conf -- sample configuration for the EPKOWA SANE backend
# Copyright (C) 2004, 2008, 2009  Olaf Meeuwissen
#
# See sane-epkowa(5), sane-usb(5) and sane-scsi(5) for details.

# Detect all devices supported by the backend.
# If you don't have a SCSI device, you can comment out the "scsi"
# keyword.  Similarly for the other keywords.
#
usb
scsi
</quote>

So I think during the upgrade that my working epkowa.conf file was renamed and a generic epkowa.conf file was substituted.


So I have now learned a lot more about how an Ubuntu Linux operating system works. :-)


:KS

---

