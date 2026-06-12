---
title: "HP C4640 Device not found Scanner"
date: 2010-04-20
forum: General Help
---

### Post by metra on 2010-04-20
Hi,

I just got a new scanner HP Photosmart C4640 and tried to set it up on Ubuntu 8.10

[SANE]("http://www.sane-project.org/cgi-bin/driver.pl?manu=hp&model=&bus=any&v=&p=") has it as supported, but I can't scan.

Printing works fine. 

when I run xsane I get ```
Failed to open device 'v4l:/dev/video0': Invalid argument.
```

Poking around I found [ScanningHowTo]("https://help.ubuntu.com/community/ScanningHowTo#What%20if%20it%20says%20%22No%20devices%20available%22?") page. But I was unable to find the .fw, .usb, or a PPD file on the CD.

Next I tried sane-find-scanner which did find the scanner```


found USB scanner (vendor=0x03f0 [HP], product=0x7411 [Photosmart C4600 series]) at libusb:003:002
```

But, this other command, which I'm not sure what it is didn't (it was part of the directions for another help post.

```

 scanimage -L
device `v4l:/dev/video0' is a Noname HP Webcam virtual device. 
```

HPLip says it doesn't support it, but I tried anyway, and nope, not supported. Couldn't even find the scanner on its own. 

That is the end of my troubleshooting capabilities and would very much appreciate some help

---

### Post by metra on 2010-04-20
:) Found my own solution.  The version of HPLip I had was 1.87xx something. Certainly not the most up to date [3.10.2]("http://hplipopensource.com/hplip-web/install/install/index.html"). HP has their own help page for installing it.

Though they did kind of gloss over the dependencies.  I needed 7 and had started to do them independently until I came up to python-devel

At that point I poked around some [more and found a great post!]("http://ubuntuforums.org/showthread.php?p=7019254#poststop") #5.

which had all the dependent files and updates already formatted to drop into a terminal.


Running the HPLip set-up allowed XSANE to find it. So, it now scans.

---

### Post by sonikk440 on 2010-05-20
I had issues with HP printer/scanners not being recognised in Karmic.
Xsane has persistently given me problems with various scanners.
I did the following two things and resolved all my issues.

1.  make sure HPLIP is up to date (if its an HP product, or course)
2.  installed simple-scan (see link below)
[http://www.ubuntugeek.com/simple-scan-a-simple-scanning-application.html](http://www.ubuntugeek.com/simple-scan-a-simple-scanning-application.html) 

Hope this helps.

---

### Post by captainron042 on 2010-11-10
I have a HP Photosmart that I got about a month ago. I had some initial problem with the printer being recognized, but I got that fixed through one of these threads.

Printing and scanning was working fine until today (possibly after an update yesterday). Today, I try to scan something, and no scanning program is finding a scanning device. It will print fine, but no scanning. 

I checked the HP troublshooting page and ran hp-check. It's telling me there's a communication problem (I think).

Can anyone help?  Below is the output of hp-check





HP Linux Imaging and Printing System (ver. 3.10.9)
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
Linux dell-desktop 2.6.32-26-generic-pae #46-Ubuntu SMP Tue Oct 26 18:18:31 UTC 2010 i686 GNU/Linux

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
HPLIP 3.10.9 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.10.9

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hplip/HP
ppdbase=/usr/share/ppd/hplip
doc=/usr/share/doc/hplip-3.10.9
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
internal-tag=3.10.9.11
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
printer_name = 
working_dir = .
device_uri = 

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[installation]
version = 3.10.9.11
date_time = 11/10/2010 12:03:12

[settings]
systray_messages = 0
systray_visible = 1

[fax]
email_address = 
voice_phone = 

[refresh]
rate = 30
enable = false
type = 1

[polling]
enable = false
device_list = 
interval = 5



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Photosmart_D110
---------------
Type: Printer
Device URI: hp:/usb/Photosmart_D110_series?serial=CN071F10C905N9
PPD: /etc/cups/ppd/Photosmart_D110.ppd
PPD Description: HP Photosmart d110 Series, hpcups 3.10.9
Printer status: printer Photosmart_D110 is idle.  enabled since Wed 10 Nov 2010 12:01:38 PM CST
error: Unsupported model: Photosmart_D110_series
error: Communication status: Failed


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
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

HP Device 0x8d11 at 001:005: 
    Device URI: hp:/usb/Photosmart_D110_series?serial=CN071F10C905N9
error: Unsupported model: Photosmart_D110_series

---------------
| USER GROUPS |
---------------

george adm lp dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev sambashare

User member of group 'lp'. Enables print/ scan/ fax.
User member of group 'lpadmin'.

-----------
| SUMMARY |
-----------

error: 1 error or warning.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.

---

