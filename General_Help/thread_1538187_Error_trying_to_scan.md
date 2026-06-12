---
title: "Error trying to scan"
date: 2010-07-24
forum: General Help
---

### Post by Alexander_Supertramp on 2010-07-24
Hi,

I've just bought a brand new HP 1050 410 All in One...
Printing is no problem, but when I try to scan a document I get the following error:

Device busy.

Although the printer/scanner is not doing anything it keeps sending me this message..


When I do a hp-check, everything looks fine:

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux HP-laptop 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux

Distribution:
ubuntu 10.04

Checking Python version...
OK, version 2.6.5 installed

Checking PyQt 4.x version...
OK, version 4.7.2 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.3
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.83.0


------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: CUPS devel- Common Unix Printing System development files...
OK, found.

Checking for dependency: CUPS image - CUPS image development files...
OK, found.

Checking for dependency: DBus - Message bus system...
OK, found.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency: libjpeg - JPEG library...
OK, found.

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
OK, found.

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
OK, found.

Checking for dependency: libusb - USB library...
OK, found.

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: PolicyKit - Administrative policy framework...
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
OK, found.

Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...
OK, found.

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 3.10.6 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.10.6

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.10.6
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=no
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=no
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=no
foomatic-drv-install=no
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.10.6.15
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
hpijs-only-build=no
lite-build=no
udev-acl-rules=yes
hpcups-only-build=no
hpijs-only-build=no


Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0



Current contents of '~/.hplip/hplip.conf' file:
error: Could not access file: No such file or directory

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                                              Model                          
  ------------------------------------------------------  -------------------------------
  hp:/usb/Deskjet_1050_J410_series?serial=CN04L1N57G05HW  HP Deskjet 1050 J410 series    

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Deskjet-1050-J410-series
------------------------
Type: Printer
Device URI: hp:/usb/Deskjet_1050_J410_series?serial=CN04L1N57G05HW
PPD: /etc/cups/ppd/Deskjet-1050-J410-series.ppd
PPD Description: HP Deskjet 1050 j410 Series, hpcups 3.10.6
Printer ready to printr Deskjet-1050-J410-series is idle.  enabled since Sat 24 Jul 2010 10:35:44 PM CEST
Communication status: Good

Deskjet_1050_J410
-----------------
Type: Printer
Device URI: hp:/usb/Deskjet_1050_J410_series?serial=CN04L1N57G05HW
PPD: /etc/cups/ppd/Deskjet_1050_J410.ppd
PPD Description: HP Deskjet 1050 j410 Series, hpcups 3.10.6
Printer status: printer Deskjet_1050_J410 is idle.  enabled since Sat 24 Jul 2010 10:34:59 PM CEST
Communication status: Good


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/Deskjet_1050_J410_series?serial=CN04L1N57G05HW' is a Hewlett-Packard Deskjet_1050_J410_series all-in-one


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.


 
-----------------
| USB I/O SETUP |
-----------------

Checking for permissions of USB attached printers...

HP Device 0x8911 at 002:003: 
    Device URI: hp:/usb/Deskjet_1050_J410_series?serial=CN04L1N57G05HW
    Device node: /dev/bus/usb/002/003
    Mode: 0664

---------------
| USER GROUPS |
---------------

root


-----------
| SUMMARY |
-----------

No errors or warnings.

Done.




I hope someone can help me with this issue!

---

### Post by darco on 2010-07-24
Try seeing if you have permission set....

Administration/User Groups/Manage Groups/

add saned if not listed

good luck

darco

---

### Post by Alexander_Supertramp on 2010-07-25
Hi,

Im in the saned group... Still no luck..

---

### Post by Kurkha on 2010-08-12
See known issues for the newest version of hplip ( [http://hplipopensource.com/node/342](http://hplipopensource.com/node/342) ):

"Scan is not supported for HP Deskjet 1050 J410 series and HP Deskjet 2050 J510 series"

---

### Post by helgesdk on 2010-10-06
There is a solution for getting DeskJet 1050 to work.
It involves editing /usr/share/hplip/data/models/models.dat
See [_this entry on launchpad_](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/652963#3).

---

