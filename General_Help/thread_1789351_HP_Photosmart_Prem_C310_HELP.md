---
title: "HP Photosmart Prem C310 HELP"
date: 2011-06-23
forum: General Help
---

### Post by 08x on 2011-06-23
OS : Ubuntu 11.04 64bit
Printer : HP Photosmart Prem C310
Connection : Wireless
Found Printer : Yes
Driver installed : Yes
Driver version : HP Photosmart Prem c310 Series, hpcups 3.11.5(en)
Device URI : hp:/net/Photosmart_Prem_C310_series?zc=HP5C2BA5
Features Working : Scan
Features NOT Working : Printing | Card Reader
Via usb Working : Printing | Scan | Card Reader
HPLIPS : Installed
HPLIPS errors : None
hp-check -t :

```
pete@pete-LT1:~/Downloads$ hp-check -t

HP Linux Imaging and Printing System (ver. 3.11.5)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies are installed to successfully compile      
HPLIP.                                                                                                                                                                                                       
2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball has the proper dependencies installed to          
successfully run.                                                                                                                                                                                            
3. Both compile- and run-time check mode (-b or --both) (Default): This mode will check both of the above cases (both compile- and run-time dependencies).                                                   

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux pete-LT1 2.6.38-10-generic #44-Ubuntu SMP Thu Jun 2 21:32:22 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Distribution:
ubuntu 11.04

Checking Python version...
OK, version 2.7.1 installed

Checking PyQt 4.x version...
OK, version 4.8.3 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.6
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.83.1


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
HPLIP 3.11.5 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.11.5

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.11.5
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
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
internal-tag=3.11.5
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
[last_used]
device_uri = "hp:/net/Photosmart_Prem_C310_series?ip=192.168.1.9"
printer_name = Photosmart_Prem_C310
working_dir = .

[installation]
date_time = 23/06/11 20:14:15
version = 3.11.5

[settings]
systray_visible = 0
systray_messages = 0

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[refresh]
rate = 30
enable = false
type = 1

[polling]
enable = false
interval = 5
device_list = 

[fax]
voice_phone = 
email_address = 



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Photosmart_Prem_C310
--------------------
Type: Printer
Device URI: hp:/net/Photosmart_Prem_C310_series?zc=HP5C2BA5
PPD: /etc/cups/ppd/Photosmart_Prem_C310.ppd
PPD Description: HP Photosmart Prem c410 Series, hpcups 3.11.5
Printer status: printer Photosmart_Prem_C310 now printing Photosmart_Prem_C310-34.  enabled since Thu 23 Jun 2011 20:11:10 BST
Communication status: Good


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/net/Photosmart_Prem_C310_series?zc=HP5C2BA5' is a Hewlett-Packard Photosmart_Prem_C310_series all-in-one


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


 
---------------
| USER GROUPS |
---------------

pete adm lp dialout cdrom plugdev lpadmin admin sambashare


-----------
| SUMMARY |
-----------

No errors or warnings.

Done.

```

---

### Post by 08x on 2011-06-24
Bump

---

### Post by 08x on 2011-06-24
Any one have any ideas?

Thanks Again

---

### Post by momist on 2011-07-25
> **08x said:**
> OS : Ubuntu 11.04 64bit
Printer : HP Photosmart Prem C310
Connection : Wireless
Found Printer : Yes
Driver installed : Yes
Driver version : HP Photosmart Prem c310 Series, hpcups 3.11.5(en)
Device URI : hp:/net/Photosmart_Prem_C310_series?zc=HP5C2BA5
Features Working : Scan
Features NOT Working : Printing | Card Reader
Via usb Working : Printing | Scan | Card Reader
HPLIPS : Installed
HPLIPS errors : None
hp-check -t :

Hi, if you're still listening.  I received my new HP Photosmart Premium e-All-In-One printer today, and have only just set it up.  I have the opposite problem to you - it prints, but won't scan.



```

---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux shelob 2.6.32-33-generic #71-Ubuntu SMP Wed Jul 20 17:27:30 UTC 2011 x86_64 GNU/Linux

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

```

And:

```

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo apt-get install --assume-yes libsane-dev

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


```

When running the HPLIP software from the HP web site, it did report that libsane_dev installation failed.  When I try to load it manually, it reports a conflict of dependencies.

However, printing works with Ubuntu 10.04, and I can't see _any_ other differences in the output you provided than my issues with libsane_dev.  Can yours be a Linux kernel or 11.04 issue?

Good luck

---

