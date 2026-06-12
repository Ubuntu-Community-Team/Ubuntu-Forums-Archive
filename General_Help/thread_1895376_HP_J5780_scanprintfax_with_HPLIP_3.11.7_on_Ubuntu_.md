---
title: "HP J5780 scan/print/fax with HPLIP 3.11.7 on Ubuntu 11.10"
date: 2011-12-14
forum: General Help
---

### Post by hihihi100 on 2011-12-14
Since the upgrade from 11.04 to 11.10 I haven't been able to scan with Xsane, but I can scan with Simplescan or with the following command:

```
 for i in `seq 1 800`; do scanimage > image$i.pnm; sleep 0; done;
```The thing with this command is I cannot change the format to jpg or pdf, it will always output it as pnm at 2 MB per page.

I need to scan 800 pages, so Xsane was and is the perfect tool. I don't know whats wrong, but anyhow, here's the output for lsb_release -a; hp-check

```
dexter@dexter-M7X0SUN:~$ lsb_release -a; hp-check
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric

HP Linux Imaging and Printing System (ver. 3.11.7)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP supplied tarball (.tar.gz or .run) to determine if the proper           
dependencies are installed to successfully compile HPLIP.                                                                                                      
2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball has 
the proper dependencies installed to successfully run.                                                                                                         
3. Both compile- and run-time check mode (-b or --both) (Default): This mode will check both of the above cases (both compile- and run-time dependencies).     

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux dexter-M7X0SUN 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux

Distribution:
ubuntu 11.10

Checking Python version...
OK, version 2.7.2 installed

Checking PyQt 4.x version...
OK, version 4.8.5 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.5.0
error_log is set to level: debug

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.84.0


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
HPLIP 3.11.7 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.11.7

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
internal-tag=3.11.7
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
[settings]
systray_visible = 2
systray_messages = 0

[last_used]
device_uri = "hp:/usb/Officejet_J5700_series?serial=CN86OCV4CM04TC"
printer_name = Fax
working_dir = .

[commands]
scan = /usr/bin/simple-scan %SANE_URI%

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

[installation]
date_time = 12/14/2011 22:08:01
version = 3.11.7



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                                            Model                          
  ----------------------------------------------------  -------------------------------
  hp:/usb/Officejet_J5700_series?serial=CN86OCV4CM04TC  HP Officejet J5700 series      

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Fax
---
Type: Fax
Device URI: hpfax:/usb/Officejet_J5700_series?serial=CN86OCV4CM04TC
PPD: /etc/cups/ppd/Fax.ppd
PPD Description: HP Deskjet 5700, hpcups 3.11.7
Printer status: printer Fax is idle.  enabled since Wed 14 Dec 2011 09:31:20 PM CET
error: Incorrect PPD file for fax queue 'Fax'. Fax queues must use 'HP-Fax-hplip.ppd'.
Communication status: Good

Officejet_J5700_series
----------------------
Type: Printer
Device URI: hp:/usb/Officejet_J5700_series?serial=CN86OCV4CM04TC
PPD: /etc/cups/ppd/Officejet_J5700_series.ppd
PPD Description: HP Officejet j5700 Series, hpcups 3.11.7
Printer status: printer Officejet_J5700_series is idle.  enabled since Wed 14 Dec 2011 09:31:20 PM CET
Communication status: Good

Officejet_J5700_series2
-----------------------
Type: Unknown
Device URI: usb://HP/Officejet%20J5700%20series?serial=CN86OCV4CM04TC&interface=1
PPD: /etc/cups/ppd/Officejet_J5700_series2.ppd
PPD Description: HP Officejet j5700 Series, hpcups 3.11.7
Printer status: printer Officejet_J5700_series2 is idle.  enabled since Wed 14 Dec 2011 09:31:20 PM CET
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
'hpaio' in '/etc/sane.d/dll.d/hplip'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/Officejet_J5700_series?serial=CN86OCV4CM04TC' is a Hewlett-Packard Officejet_J5700_series all-in-one


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

HP Device 0x5b11 at 001:003: 
    Device URI: hp:/usb/Officejet_J5700_series?serial=CN86OCV4CM04TC
    Device node: /dev/bus/usb/001/003
    Mode: 0664
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/001/003
# owner: root
# group: lp
user::rw-
user:dexter:rw-
group::rw-
mask::rw-
other::r--



---------------
| USER GROUPS |
---------------

dexter adm lp dialout cdrom plugdev lpadmin admin sambashare

User member of group 'lp'. Enables print/ scan/ fax.
User member of group 'lpadmin'.

-----------
| SUMMARY |
-----------

error: 2 errors and/or warnings.

Please refer to the installation instructions at:
http://hplip.sourceforge.net/install/index.html


Done.
dexter@dexter-M7X0SUN:~$ 

```Help appreciated

Xsane sends the order to the scanner to scan, and it does so, it even creates a .jpg file in the directory I want, with different sizes depending on each page, but when I use any image viewer all I see is black background against a single white vertical line

---

