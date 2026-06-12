---
title: "HP Officejet 6500 e710n Printer; getting scanner to work."
date: 2011-01-17
forum: General Help
---

### Post by akand074 on 2011-01-17
Hey guys:

I saw this on a review on the HP website for the e709n (one version older)

>  "I  bought an Officejet 6500 E709n a few days ago, and am so far very  satisfied with it. I set it up, including its wireless functionality,  painlessly using Windows XP, but actually use it with ubuntu linux. I'm  not using its fax capabilities, just print/copy/scan.
Basically,  I'm used to having to struggle a bit when installing a new device on a  linux system. This has so far not been the case with the 6500. Even  2-sided printing worked immediately.
I  don't understand the comments about slow scanning. I'm using XSane Vn  0.996 and it scans just fine. Obviously the scanning gets slower if you  up the resolution, but one expects such things. Maybe I'm too  uncritical!
If  one wants to get picky about a CHF 250 all-in-one device, it does clunk  and whirr rather excessively, especially after a print job, and I  expected 2-sided copy to turn the original over automatically for me,  which it doesn't. But a print job is quick to start, contrary to other  reviewers' remarks, and its print speed is OK for home use."

 
But I haven't been able to get my scanner to work. I followed the instructions from [this ]("https://help.ubuntu.com/community/HpAllInOne")site, but HP-Setup won't even find my printer. But when I just plug it in via usb it finds it and installs the drivers so printing works, but simple scanner/xsane still can't find the scanner. I ran HP-Check and it had 9 errors with libs and development files I installed like over 200MB of dev files I could find that related to what they had from synaptic package manager and I managed to bring it down to two errors. In the HP check it does say "error: Unsupported model: Officejet_6500_E710n-z" which could mean maybe this new version isn't supported yet.. but I mean it's found and drivers installed just fine for printing when I plug it in. Here is my most recent HP-check:

```
HP Linux Imaging and Printing System (ver. 3.10.6)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies
are installed to successfully compile HPLIP.                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro    
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball   
has the proper dependencies installed to successfully run.                      
3. Both compile- and run-time check mode (-b or --both) (Default): This mode    
will check both of the above cases (both compile- and run-time dependencies).   

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux andrew-desktop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux

Distribution:
ubuntu 10.10

Checking Python version...
OK, version 2.6.6 installed

Checking PyQt 4.x version...
OK, version 4.7.4 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.4
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
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

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
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

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
ppd=/usr/share/ppd/hplip/HP
ppdbase=/usr/share/ppd/hplip
doc=/usr/share/doc/hplip-doc/HTML
icon=no
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=yes
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=yes
foomatic-drv-install=yes
foomatic-ppd-install=yes
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.10.6.15
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes
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
[installation]
version = 3.10.6.15
date_time = 11-01-17 18:53:18



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
lpstat
------
Type: Unknown
Device URI: No destinations added.


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
'hpaio' in '/etc/sane.d/dll.d/hplip'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


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

HP Device 0x5412 at 002:005: 
    Device URI: hp:/usb/Officejet_6500_E710n-z?serial=CN0AL123T905JW
error: Unsupported model: Officejet_6500_E710n-z

---------------
| USER GROUPS |
---------------

andrew adm dialout cdrom plugdev lpadmin admin sambashare

error: User needs to be member of group 'lp' to enable print, scan & fax.
User member of group 'lpadmin'.

-----------
| SUMMARY |
-----------

error: 2 errors and/or warnings.

Please refer to the installation instructions at:
http://hplip.sourceforge.net/install/index.html


Done.

```Anyone have any input on how to get the scanner to work, or if it is indeed not supportet yet? Thanks for any help!

EDIT: I just plugged my printer out/and back in after having deleted it from the printing menu and it turns out it had me install the e709n printer drivers for it.. so perhaps printing is the same but I need to wait for the new drivers to get scanning?

---

### Post by akand074 on 2011-01-18
I'll give it a bump.

---

### Post by ArgAthens on 2011-02-02
It looks like support for that printer wasn't included until 3.10.9 which is more recent than the installed version in Ubuntu 10.10. 

I pulled down the tarball for 3.11.1 and tried to manually attach the ppd to the printer which didn't work.  I then download the 3.11.1 builder from [http://sourceforge.net/projects/hplip/](http://sourceforge.net/projects/hplip/) which worked.  

It found the printer and installed all of the drivers correctly, it's actually a really sweet setup.  I can now scan, fax, print, etc.

---

### Post by Hedon James on 2011-03-18
> **ArgAthens said:**
> It looks like support for that printer wasn't included until 3.10.9 which is more recent than the installed version in Ubuntu 10.10. 

I pulled down the tarball for 3.11.1 and tried to manually attach the ppd to the printer which didn't work.  I then download the 3.11.1 builder from [http://sourceforge.net/projects/hplip/](http://sourceforge.net/projects/hplip/) which worked.  

It found the printer and installed all of the drivers correctly, it's actually a really sweet setup.  I can now scan, fax, print, etc.

Are you able to use the ADF for scanning?  If so, I'm jealous.

I'm at my wit's end with this machine.  Looking for assistance on launchpad, but wondered if any of you "successful installers" can help out?  Copy of launchpad post as follows:

New question #149573 on HPLIP:
[https://answers.launchpad.net/hplip/+question/149573](https://answers.launchpad.net/hplip/+question/149573)

I am unable to scan from the ADF.

I have previously used Simple Scan and gscan2pdf for scanning documents.  With my previous scanner, there was an option to scan from "flatbed" or "ADF".  While I have not previously utilized XSane, as invoked by the HPLIP printer "scan" option, XSane defaults to a "flatbed" scan also.  Why can't I select ADF as my source?

It appears the Officejet 6500A only provides for "flatbed" scanning; the ADF is not recognized, despite HP representation of full support for ADF document scanning.  While the ADF is able to copy a multi-page document, it is not able to scan; the machine just "hangs".  Single page scans from the flatbed are fine.  However, inasmuch as I purchased the Officeject 6500A based on HP reputation for linux-compatibilty AND its 35 sheet ADF capacity, the lack of ADF scanning is a deal-breaking problem!

As additional background for troubleshooting, I have successfully installed the HP Officejet 6500A (model E710A) on my Ubuntu 10.04 desktop.  The HPLIP Status Service displays in the notification area, with appropriate Officejet Printer & Fax devices.  Both devices also appear in my print manager.  I am able to print to the device, although my intentions were to use it solely as a scanner.  I haven't bothered with fax setup, as I don't care about that feature.

I have followed the hplip 3.11.3 download/installation/setup instructions to the letter.  Everything appears to be working appropriately, except the only feature I care about...ADF scanning.  If the ADF feature didn't work for COPYING, I'd think the ADF was faulty.

Have I missed something?  I really like this machine and want to make it work.  HP has a good reputation with the linux community for providing linux-compatible drivers, but this is my first HP purchase.  Please show me that the linux community was correct to recommend HP as a hardware vendor!  THANK YOU!

[FONT=Verdana]While I'm waiting for launchpad support I may never receive, anyone here solved this problem before?  Thanks for reading...

[/FONT]

---

### Post by Hedon James on 2011-03-20
as a follow up to my previous post, a launchpad respondent indicates they have the same ADF issue and are waiting for the feature to be addressed.  Although HP hasn't responded to my inquiry, the respondent indicates HP told him they're "working on the issue".

Inasmuch as the HP website indicates the Officejet6500A linux driver is fully-featured, I'm extremely disappointed at the false advertising.

FWIW, and to share this knowledge with others, I exchanged the 2-day old HP Officejet for an Epson Workforce 630 (added bonus...1/2 the price!).  I don't know how to post a link, but I found this printer here on the Ubuntu forum by searching "Ubuntu Epson Workforce 630" in google. Apparently, AVASYS provides proprietary drivers & software for this machine.  Yeah, I know "proprietary"...if you're an open source zealot, this isn't for you; but if you want it to "just work", I highly recommend you look into it.

The Epson Workforce 630 is AWESOME!  Easiest linux hardware setup I've ever done.  Downloaded the driver, downloaded the software files, installed everything, connected the printer and boom...it just worked!  Extremely pleased and just wanted to share the info with other frustrated users.

---

