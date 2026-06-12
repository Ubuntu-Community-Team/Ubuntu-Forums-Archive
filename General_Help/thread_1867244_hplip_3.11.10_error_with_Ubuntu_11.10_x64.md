---
title: "hplip 3.11.10 error with Ubuntu 11.10 x64"
date: 2011-10-22
forum: General Help
---

### Post by Oless on 2011-10-22
After installing hplip 3.11.10 and running hp-setup I got error in terminal 

[I](python:1965): Gtk-WARNING **: Unable to locate theme engine in  module_path: "pixmap",
Searching... (bus=usb, search=(None), desc=0)
error:  The printer you are trying to setup requires a binary driver plug-in and it failed to install.  Please check your internet connection and try again.  Visit  [http://hplipopensource.com](http://hplipopensource.com)  for more infomation. 
Searching... (bus=usb, search=(None), desc=0)[/I]

running *hp-setup -g*

got this 

[I]Traceback (most recent call last):
  File "/usr/bin/hp-setup", line 45, in <module>
    from base import device, utils, tui, models, module
  File "/usr/share/hplip/base/device.py", line 39, in <module>
    import status
  File "/usr/share/hplip/base/status.py", line 45, in <module>
    import hpmudext
ImportError: libhpmud.so.0: cannot open shared object file: No such file or directory[/I]

solution found in [https://answers.launchpad.net/hplip/+question/174891](https://answers.launchpad.net/hplip/+question/174891)  to add in file /home/myusrname/.bashrc following lines

 LD_LIBRARY_PATH=/usr/lib64/:$LD_LIBRARY_PATH
 export LD_LIBRARY_PATH


does not work


hp-check tells following:


HP Linux Imaging and Printing System (ver. 3.11.10)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling   
the HPLIP supplied tarball (.tar.gz or .run) to determine if the proper        
dependencies are installed to successfully compile HPLIP.                      
2. Run-time check mode (-r or --run): Use this mode to determine if a distro   
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball  
has the proper dependencies installed to successfully run.                     
3. Both compile- and run-time check mode (-b or --both) (Default): This mode   
will check both of the above cases (both compile- and run-time dependencies).  

Saving output in log file: hp-check.log

Initializing. Please wait...
-
(hp-check:2013): Gtk-WARNING **: Neizdev?s atrast t?mu dzin?ju module_path: "pixmap",
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux oless-Aspire 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Distribution:
ubuntu 11.10

Checking Python version...
OK, version 2.7.2 installed

Checking PyQt 4.x version...
OK, version 4.8.5 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.5.0
error_log is set to level: warn

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
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.
To install this dependency, execute this command:
sudo apt-get install --assume-yes xsane


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 3.11.10 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.11.10

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.11.10
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
internal-tag=3.11.10
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
[installation]
date_time = 2011.10.22. 22:39:26
version = 3.11.10



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                       Model            
  -------------------------------  -----------------
  hp:/usb/HP_LaserJet_P1005?seria  HP LaserJet P1005
  l=BC1KAWJ                                         

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
HP-LaserJet-P1005
-----------------
Type: Unknown
Device URI: usb://HP/LaserJet%20P1005?serial=BC1KAWJ
PPD: /etc/cups/ppd/HP-LaserJet-P1005.ppd
PPD Description: HP LaserJet P1005 Foomatic/foo2xqx (recommended)
Printer status: printer HP-LaserJet-P1005 is idle.  enabled since sestdiena, 2011. gada 22. oktobris, plkst. 21 un 16
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.


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

HP Device 0x3d17 at 002:002: 
    Device URI: hp:/usb/HP_LaserJet_P1005?serial=BC1KAWJ

HP Linux Imaging and Printing System (ver. 3.11.10)
System Tray Status Service ver. 2.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


(hp-systray:2051): Gtk-WARNING **: Neizdev?s atrast t?mu dzin?ju module_path: "pixmap",
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
    Device node: /dev/bus/usb/002/002
    Mode: 0664
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/002/002
# owner: root
# group: lp
user::rw-
user:oless:rw-
group::rw-
mask::rw-
other::r--



---------------
| USER GROUPS |
---------------

oless adm lp dialout cdrom plugdev lpadmin admin sambashare


-----------
| SUMMARY |
-----------

error: 2 errors and/or warnings.

Summary of needed commands to run to satisfy missing dependencies:
sudo apt-get install --assume-yes xsane

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

---

### Post by LowSky on 2011-10-22
go here:
[http://localhost:631/](http://localhost:631/)

add printer from here instead. will work fine.use foomtic driver

---

### Post by Oless on 2011-10-22
not working anyway

---

### Post by xand on 2011-10-24
same problem here :/

---

### Post by robwire on 2011-10-25
Same problem here :(

---

### Post by rsrini on 2011-10-31
Using P1007 printer. **[SIZE=2]While installing hplip 3.11.10 i got the error message[/SIZE]** 

(PRINTER SETUP
-------------
Please make sure your printer is connected and powered on at this time.
error: hp-setup failed. Please run hp-setup manually.)

**[SIZE=2]I ran the "hp-check -r" command and got the following error. [/SIZE]**

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
error: NOT FOUND OR FAILED TO LOAD! Please reinstall HPLIP and check for the proper installation of hpmudext.

Checking 'scanext' SANE scanning extension...
OK, found.
-----------
| SUMMARY |
-----------

error: 3 errors and/or warnings.

R.Srinivasan

---

### Post by love2learn on 2011-11-02
same problem here. I will keep an eye out.

**update**  post #3 #4 and #5  from [https://answers.launchpad.net/hplip/+question/174891](https://answers.launchpad.net/hplip/+question/174891)   got hp-setup to work for me. 

Specifically:

[I]The work around for this is
open terminal and type in the below command:
"export  LD_LIBRARY_[/I]*PATH=$LD_**LIBRARY_**PATH:/usr/**lib64/"*
*Next run, "hp-setup" command in the same terminal and check whether you get the same ImportError*



if hp-setup runs after that then do the permanent solution below:


[I]To have this variable permanently set you need to edit the file .bashrc present in your  home folder ($HOME).
Go to you home directory ( $cd  ~)
edit the file  .bashrc (  $vim .bashrc)
enter the below lines at the end of the file and save it and close it[/I] *LD_LIBRARY_PATH = $LD_LIBRARY_**PATH:/usr/*[I]lib64/
export LD_LIBRARY_PATH[/I]

[I]After that restart your system and check running "hp-setup"

[/I]This worked for me asus N53SV, kubuntu 11.10 64 , and hp deskjet 3050.

Thanks goes to [goutamkk (goutam-hplip) ]("https://launchpad.net/%7Egoutam-hplip")

---

