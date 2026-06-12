---
title: "HP LaserJet Professional P1606dn - Required plugin not found"
date: 2011-01-27
forum: General Help
---

### Post by Quoom2eiye on 2011-01-27
Hi all,

I'm new to Linux and I love it so far. But tonight, I tried to print something to realize that I cannot print!

I have a HP LaserJet Professional P1606dn that is linked to my network. I installed HPLIP and managed to configure my printer. I know I can communicate with the printer since I can see its status and all. However, every time I print, I get a message that the HP device manager cannot find a required plugin...

From CUPS, i can see that the Driver is "HP LaserJet Professional p1606dn hpijs, 3.10.6, requires proprietary plugin (color, 2-sided printing)" and if I go through the Synaptic Package Manager, I can see that the packet "HP Linux Printing and Imaging - gs IJS driver (hpijs)" version 3.10.6-1ubuntu10.2 is installed...

Maybe a path somewhere is wrong? Help!

Cheers![INDENT]olivier@olivier:~$ hp-check -r

```

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
Linux olivier 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux

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


------------------------
| RUNTIME DEPENDENCIES |
------------------------


Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: PolicyKit - Administrative policy framework...
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...
OK, found.

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.


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
scanner-build=no
fax-build=no
dbus-build=no
cups11-build=no
doc-build=no
shadow-build=no
hpijs-install=yes
foomatic-drv-install=no
foomatic-ppd-install=yes
foomatic-rip-hplip-install=no
hpcups-install=no
cups-drv-install=no
cups-ppd-install=no
internal-tag=3.10.9.11
restricted-build=no
ui-toolkit=no
qt3=no
qt4=no
policy-kit=no
hpijs-only-build=no
lite-build=no
udev-acl-rules=no
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
device_uri = "hp:/net/HP_LaserJet_Professional_P1606dn?zc=Home_Sweet_Home"

[commands]
scan = /usr/bin/simple-scan %SANE_URI%

[installation]
version = 3.10.9.11
date_time = 11-01-27 22:52:13

[settings]
systray_messages = 0
systray_visible = 0

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
 
Home-Sweet-Home-Print
---------------------
Type: Printer
Device URI: hp:/net/HP_LaserJet_Professional_P1606dn?zc=Home_Sweet_Home
PPD: /etc/cups/ppd/Home-Sweet-Home-Print.ppd
PPD Description: HP LaserJet Professional p1606dn hpijs, 3.10.6, requires proprietary plugin
Printer status: printer Home-Sweet-Home-Print is idle.  enabled since Thu 27 Jan 2011 10:45:30 PM EST
[COLOR=Red]**warning: Optional plug-in status: Not installed**[/COLOR]
Communication status: Good


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

 
---------------
| USER GROUPS |
---------------

olivier adm lp dialout cdrom plugdev lpadmin admin sambashare

User member of group 'lp'. Enables print/ scan/ fax.
User member of group 'lpadmin'.

-----------
| SUMMARY |
-----------

error: 3 errors and/or warnings.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.


[/INDENT]

```

---

### Post by drs305 on 2011-01-31
I'd been getting the HP Printer Driver Plug-in message for the past week or so, even though my printer was working fine. I'd reinstalled the drivers via Synaptic, and also ran "hp-setup" and "hp-plugin" numerous times. 

As with you, I was using 3.10.9. I went to the HP site, linked below, ran through their questionnaire and it downloaded *hplip-3.11.1.run*  The site showed the installation screens and it ran a much more comprehensive set up than any other command line method I'd used.

It uninstalled all my currently-installed printer drivers using:
> 
sudo apt-get remove --assume-yes hplip hpijs hplip-cups hplip-data libhpmud0 foomatic-db-hpijs (Removing old HPLIP version)
I enclosed this as a quote rather than as a command, as it is done as part of the installation script and you need not accomplish this separately.

At completion, I no longer get the plug-in message. Perhaps you will have similar success.

[http://hplipopensource.com/hplip-web/install_wizard/index.html]("http://hplipopensource.com/hplip-web/install_wizard/index.html")


Note: I edited your post to make the formatting a bit more user friendly. I enclosed the output in [noparse]```
  
```[/noparse] tags, which you generate by pressing the **#** icon in the post's menubar. Then paste the contents between the tags.

---

### Post by Quoom2eiye on 2011-01-31
It works!

I've downloaded and run the HPLIP-3.1.11.run from your link. Everything works perfectly now.

Many thanks.

---

### Post by Padakwaak on 2011-06-28
Thanks drs305!

Your post really saved my day - I also struggled with the "plug-in status: Not installed" issue with my office's HP M1522nf MFP.

---

### Post by zandoval on 2011-10-04
Found a fix for Ubuntu based Linux Mint - Just give it a try...

Make sure HPLIP is installed

Delete any old attempted installs of the 1606

Unplug the usb

Unplug the Printer

Shut down computer

Restart computer and then shut it down again

Plug in usb and printer power

Restart the computer

I rally don't know why this works and I don't know if it works in other than Mint...

Here is a link
[http://forums.linuxmint.com/viewtopic.php?f=49&t=51644&p=480094#p480094](http://forums.linuxmint.com/viewtopic.php?f=49&t=51644&p=480094#p480094)

---

### Post by skliarie on 2011-12-13
On my ubuntu 11.10 machine, the printer is discovered under some unusual URL: dnssd://HP%20LaserJet%20Professional%20P1606dn._pdl-datastream._tcp.local/

And when I run "hp-check -r", I get the following output:
```
HP1606dn
--------
Type: Unknown
Device URI: dnssd://HP%20LaserJet%20Professional%20P1606dn._pdl-datastream._tcp.local/
PPD: /etc/cups/ppd/HP1606dn.ppd
PPD Description: HP LaserJet Professional p1606dn hpijs, 3.11.1, requires proprietary plugin                                                                   Printer status: printer HP1606dn is idle.  enabled since Mon 12 Dec 2011 11:12:36 AM IST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.
```

hp-firmware does not detect the printer as well:
```
...
hp-firmware[7150]: debug: Starting GUI loop...
hp-firmware[7150]: debug: Device URI dnssd://HP%20LaserJet%20Professional%20P1606dn._pdl-datastream._tcp.local/ is invalid/unknown
hp-firmware[7150]: debug: Exception: 4 (Unknown/invalid device-uri field)
...

```

Is there anything special in the way the printer should broadcast itself for cups to recognize it properly?

---

### Post by milany on 2012-03-22
I had a similar problem with linux mint (ubuntu based).

It appears that HP has catered to the windows crowd.  After much head banging, I found out that the printer is claiming to be a CD ROM drive when plugged into a usb port.

if you unplug your printer, then plug it back in, and type dmesg at a shell prompt,
and it looks like you have a new scsi drive, this may help.

I had previously followed HP's advice and went to the hplip site to install the printer.  I rebuilt the driver a gazillion times, installing packages that probably weren't necessary.

It would work up to the point where it would search for the printer on the usb bus, but it could not find the printer; but if I specified the usb bus and device ( e.g 002:002) it would see the printer, but when I went to print, it would not work.

Turns out, that you need to run a utility to disable the stupid cd-rom spoofing in windows.
see this site for details.
[https://bugs.launchpad.net/hplip/+bug/951763](https://bugs.launchpad.net/hplip/+bug/951763)

After I did this, the printer was found and installed fine.  I haven't had any issues to date.

Shame on HP!

---

