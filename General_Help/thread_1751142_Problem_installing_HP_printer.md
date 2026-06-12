---
title: "Problem installing HP printer"
date: 2011-05-06
forum: General Help
---

### Post by layers on 2011-05-06
I am trying to install the drivers for this unsupported printer: HP LaserJet P1102w.

I do not understand the dependecy errors: I do have gcc, for instance, if I can compile with gcc program.c, right?

```
ibo@ibo-laptop:~$ jobs -l
ibo@ibo-laptop:~$ cd Downloads/
ibo@ibo-laptop:~/Downloads$ sh run hplip-3.11.3a
sh: Can't open run
ibo@ibo-laptop:~/Downloads$ sh hplip-3.11.3a
sh: Can't open hplip-3.11.3a
ibo@ibo-laptop:~/Downloads$ sh hplip-3.11.3a run
sh: Can't open hplip-3.11.3a
ibo@ibo-laptop:~/Downloads$ sudo sh hplip-3.11.3a run
[sudo] password for ibo: 
ibo@ibo-laptop:~/Downloads$ ls
firefox  firefox-4.0.1.tar.bz2  hplip-3.11.3a  hplip-3.11.3a.run
ibo@ibo-laptop:~/Downloads$ sh hplip-3.11.3a.run
Creating directory hplip-3.11.3a
Verifying archive integrity... All good.
Uncompressing HPLIP 3.11.3a Self Extracting Archivedf: `hplip-3.11.3a': Permission denied
df: no file systems processed
test: 365: -lt: unexpected operator
cd: 379: can't cd to hplip-3.11.3a
.......................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................cd: 379: can't cd to hplip-3.11.3a
chown: cannot read directory `./hplip-3.11.3a': Permission denied
chgrp: cannot read directory `./hplip-3.11.3a': Permission denied

cd: 382: can't cd to hplip-3.11.3a

HP Linux Imaging and Printing System (ver. 3.11.3a)
HPLIP Installer ver. 5.1

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Fri-06-May-2011_10:03:15.log

/
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.


INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to choose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : a

Initializing. Please wait...
 

INTRODUCTION
------------
This installer will install HPLIP version 3.11.3a on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).


DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 9.10.

Is "Ubuntu 9.10" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y


ENTER USER PASSWORD
-------------------
Please enter the user (ibo)'s password: 
Password accepted


INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: https://help.ubuntu.com/community/Repositories/Ubuntu for more information.  Disable the CD-ROM/DVD source if you do not have the Ubuntu installation media inserted in the drive.  During the install process you will be added to the lp group, please quit the installer before the setup stage, log out, log back in, and run hp-setup to complete the install.

Please read the installation notes. Press <enter> to continue or 'q' to quit: 


RUNNING PRE-INSTALL COMMANDS
----------------------------
OK


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 7 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: Missing REQUIRED dependency: python-devel (Python devel - Python development files)
warning: Missing REQUIRED dependency: cups-devel (CUPS devel- Common Unix Printing System development files)
warning: Missing REQUIRED dependency: libusb (libusb - USB library)
warning: Missing REQUIRED dependency: libtool (libtool - Library building support services)
warning: Missing REQUIRED dependency: cups-image (CUPS image - CUPS image development files)
warning: Missing REQUIRED dependency: libjpeg (libjpeg - JPEG library)


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 8 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'network': libcrypto (libcrypto - OpenSSL cryptographic library)
warning: Missing REQUIRED dependency for option 'network': libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)
warning: Missing REQUIRED dependency for option 'gui_qt4': pyqt4-dbus (PyQt 4 DBus - DBus Support for PyQt4)
warning: Missing REQUIRED dependency for option 'gui_qt4': pyqt4 (PyQt 4- Qt interface for Python (for Qt version 4.x))
warning: Missing OPTIONAL dependency for option 'fax': reportlab (Reportlab - PDF library for Python)
warning: Missing REQUIRED dependency for option 'fax': dbus (DBus - Message bus system)
warning: Missing REQUIRED dependency for option 'scan': sane-devel (SANE - Scanning library development files)
warning: Missing OPTIONAL dependency for option 'base': cups-ddk (CUPS DDK - CUPS driver development kit)


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.


RUNNING PRE-PACKAGE COMMANDS
----------------------------
sudo dpkg --configure -a (Pre-depend step 1)
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
sudo apt-get update (Pre-depend step 3)
OK


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --assume-yes build-essential'
Please wait, this may take several minutes...
error: Command failed. Re-try #1...
Running 'sudo apt-get install --assume-yes build-essential'
Please wait, this may take several minutes...
error: Command failed. Re-try #2...
Running 'sudo apt-get install --assume-yes build-essential'
Please wait, this may take several minutes...
error: Command failed. Re-try #3...
Running 'sudo apt-get install --assume-yes build-essential'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ?   

```

---

### Post by layers on 2011-05-06
If I try my self:
```
ibo@ibo-laptop:~$ sudo apt-get update
[sudo] password for ibo: 
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                 
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US             
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com karmic Release                                
Hit http://us.archive.ubuntu.com karmic/main Packages                          
Hit http://us.archive.ubuntu.com karmic/restricted Packages                
Hit http://us.archive.ubuntu.com karmic/main Sources                           
Hit http://us.archive.ubuntu.com karmic/restricted Sources                     
Hit http://us.archive.ubuntu.com karmic/universe Packages                      
Hit http://us.archive.ubuntu.com karmic/universe Sources                       
Hit http://us.archive.ubuntu.com karmic/multiverse Packages                    
Hit http://us.archive.ubuntu.com karmic/multiverse Sources                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://archive.canonical.com karmic Release.gpg
Ign http://archive.canonical.com karmic/partner Translation-en_US
Hit http://ppa.launchpad.net karmic Release    
Hit http://archive.canonical.com karmic Release                     
Hit http://ppa.launchpad.net karmic Release                         
Hit http://ppa.launchpad.net karmic/main Packages                   
Hit http://archive.canonical.com karmic/partner Packages            
Hit http://ppa.launchpad.net karmic/main Packages
Reading package lists... Done
ibo@ibo-laptop:~$ sudo apt-get install gcc g++ libc6 make python-dev libcupsys2-dev cupsys-bsd libusb-dev libtool libjpeg62-dev libssl-dev libsnmp9-dev python-reportlab libsane-dev libsane
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
libc6 is already the newest version.
make is already the newest version.
Note, selecting libcups2-dev instead of libcupsys2-dev
Note, selecting libsnmp-dev instead of libsnmp9-dev
libsane is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  g++: Depends: g++-4.4 (>= 4.4.1-1) but it is not going to be installed
  libcups2-dev: Depends: libcups2 (= 1.4.1-5ubuntu2) but 1.4.1-5ubuntu2.7 is to be installed
  libsane-dev: Depends: libtiff4-dev but it is not going to be installed
               Depends: libavahi-client-dev but it is not going to be installed
  libssl-dev: Depends: libssl0.9.8 (= 0.9.8g-16ubuntu3) but 0.9.8g-16ubuntu3.5 is to be installed
  python-dev: Depends: python (= 2.6.4~rc1-0ubuntu1) but 2.6.4-0ubuntu1 is to be installed
              Depends: python2.6-dev (>= 2.6.4~rc1) but it is not going to be installed
E: Broken packages
ibo@ibo-laptop:~$ 

```

How should I proceed?

---

