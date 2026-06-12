---
title: "Cant get printer setup right"
date: 2010-09-15
forum: General Help
---

### Post by ngardner on 2010-09-15
Im running Ubuntu 10.04 LTS and cannot get my new printer working correctly. The printer is a HP Photosmart D110. When I added the printer - everything seemed to go smoothly. It found the right drivers (HP-PHOTO-D100series) and everything automatically, but when I got to the print test page, it only printed on the top left corner of the page.

I noticed on the print test page it said "Media Dimensions: 4x6 inches". I found the setting for the "Media Size" setting, but there are no options for Letter, Legal, or even A6. All the options are for photos / cds, and whatever a hagaki is.

I choose "custom" but there is no where to type in a size - and when I try printing then, it just fails and prints an empty page.

It says "HP Photosmart 100 hpijs, 3.10.2" next to make / model, even though its a D110

Please help!

---

### Post by linuxonbute on 2010-09-17
> **ngardner said:**
> Im running Ubuntu 10.04 LTS and cannot get my new printer working correctly. The printer is a HP Photosmart D110. When I added the printer - everything seemed to go smoothly. It found the right drivers (HP-PHOTO-D100series) and everything automatically, but when I got to the print test page, it only printed on the top left corner of the page.

I noticed on the print test page it said "Media Dimensions: 4x6 inches". I found the setting for the "Media Size" setting, but there are no options for Letter, Legal, or even A6. All the options are for photos / cds, and whatever a hagaki is.

I choose "custom" but there is no where to type in a size - and when I try printing then, it just fails and prints an empty page.

It says "HP Photosmart 100 hpijs, 3.10.2" next to make / model, even though its a D110

Please help!
have you looked here [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) ?

maybe it will solve your problem. Look especially at the troubleshooting pages.

---

### Post by captainron042 on 2010-10-07
I'm also having a problem with this printer. It printed test page just fine on setup, even printed from Openoffice. 

I tried to scan, and Ubuntu can't find any devices. I tried updating HPLIP from the link above, and I get an error "error: Configure failed with error: python-devel not found"

Now it won't print anymore, either

---

### Post by Locke_99GS on 2010-10-07
I love my HP d110 printer. Awesome printer for the low-low price :p I had to use the current hplip from hplipopensource.com. I didn't have any problems on 10.04. Have you tried installing the missing package?

```

sudo aptitude install python-dev

```

I did not have this message, but I compile a lot of things and may have had it installed already. Any more specific issues?

---

### Post by captainron042 on 2010-10-07
Dude, you are awesome! I've been pulling my hair for 3 hours now! I'd take your Dropbox referral, if I wasn't already using it!

---

### Post by Locke_99GS on 2010-10-07
So I reckon it worked then? If so, I'm just glad it was that simple. It's horrible when things *should* work, and they don't. That leads to a whole new level of headache.

edit: The Dropbox referral is part of my sig. I've nearly maxed out the bonus space. I'll switch it to my wifes referral soon. :) The second one is my fancy auto-update-mahigy. (cheap plug)

---

### Post by captainron042 on 2010-10-07
Yes, it worked!

---

### Post by ngardner on 2010-10-15
Upgraded to 10.10, uninstalled and reinstalled the printer - and now its works perfect!

---

### Post by DougLawson on 2010-10-21
Thank-you for the link.  This worked perfectly for me!

---

### Post by colinmccubbin on 2010-12-28
> **Locke_99GS said:**
> I love my HP d110 printer. Awesome printer for the low-low price :p I had to use the current hplip from hplipopensource.com. I didn't have any problems on 10.04. Have you tried installing the missing package?

```

sudo aptitude install python-dev

```

I did not have this message, but I compile a lot of things and may have had it installed already. Any more specific issues?

I'm having the same message: **"error: Configure failed with error: python-devel not found"** when trying to install my new HP photosmart C410 multifunction printer.. Which I bought specifically BECAUSE hp's website says all the functions work under Ubuntu..

My question is 'why do you say python-dev is needed when the failure refers to python-devel'?

I'm fairly 'new' to Ubuntu (using 9.05) and have played around a bit with python, both v 2.6.4 (the Ubuntu default) and 3.1 which I added recently since the tutorial book I bought uses python3.  I don't really understand why hp's .run file doesn't just call any dependencies it is missing.

Any help would be most welcome!

Thanks,

---

### Post by colinmccubbin on 2010-12-28
I tried running **sudo aptitude install python-dev** and then ./hplip-3.10.9.run   IT WORKED THIS TIME! Many thanks indeed.

Tried printing, and scanning, both work.



```
colin@Quiet-box:~/Downloads$ ./hplip-3.10.9.run
Creating directory hplip-3.10.9
Verifying archive integrity... All good.
Uncompressing HPLIP 3.10.9 Self Extracting Archive.............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

HP Linux Imaging and Printing System (ver. 3.10.9)
HPLIP Installer ver. 5.1

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Tue-28-Dec-2010_16:19:00.log

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
This installer will install HPLIP version 3.10.9 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).
 

DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 9.10.

Is "Ubuntu 9.10" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y


ENTER USER PASSWORD
-------------------
Please enter the user (colin)'s password: 
Password accepted


INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: https://help.ubuntu.com/community/Repositories/Ubuntu for more information.  Disable the CD-ROM/DVD source if you do not have the Ubuntu installation media inserted in the drive.  During the install process you will be added to the lp group, please quit the installer before the setup stage, log out, log back in, and run hp-setup to complete the install.

Please read the installation notes. Press <enter> to continue or 'q' to quit: 


RUNNING PRE-INSTALL COMMANDS
----------------------------
OK


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.


RUNNING PRE-PACKAGE COMMANDS
----------------------------
sudo dpkg --configure -a (Pre-depend step 1)
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
sudo aptitude update (Pre-depend step 3)
OK


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
warning: A previous install of HPLIP is installed and/or running.
sudo apt-get remove --assume-yes hplip hpijs hplip-cups hplip-data libhpmud0 foomatic-db-hpijs (Removing old HPLIP version)
warning: HPLIP removal failed. The previous install may have been installed using a tarball or this installer.
warning: Continuing to run installer - this installation should overwrite the previous one.


RUNNING POST-PACKAGE COMMANDS
-----------------------------
OK


RE-CHECKING DEPENDENCIES
------------------------
OK


PRE-BUILD COMMANDS
------------------
OK


BUILD AND INSTALL
-----------------
Running './configure --with-hpppddir=/usr/share/ppd/HP --prefix=/usr --enable-udev-acl-rules --enable-qt4 --enable-doc-build --disable-cups-ppd-install --disable-foomatic-drv-install --disable-foomatic-ppd-install --disable-hpijs-install --enable-policykit --enable-cups-drv-install --enable-hpcups-install --enable-network-build --enable-dbus-build --enable-scan-build --enable-fax-build'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make clean'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make'
Please wait, this may take several minutes...
Command completed successfully.

Running 'sudo make install'
Please wait, this may take several minutes...
Command completed successfully.


Build complete.


POST-BUILD COMMANDS
-------------------
sudo sh /etc/init.d/dbus reload (Post-build step 1)
sudo /usr/sbin/usermod -a -Glp colin (Post-build step 2)


CLOSE HP_SYSTRAY
----------------
Sending close message to hp-systray (if it is currently running)...


RESTART OR RE-PLUG IS REQUIRED
------------------------------
If you are installing a USB connected printer, and the printer was plugged in when you started this installer, you will need to either restart your PC or    
unplug and re-plug in your printer (USB cable only). If you choose to restart, run this command after restarting: hp-setup (Note: If you are using a parallel
connection, you will have to restart your PC. If you are using network/wireless, you can ignore and continue).                                               

Restart or re-plug in your printer (r=restart, p=re-plug in*, i=ignore/continue, q=quit) :
```

I restarted, opened terminal again, ran: hp-setup

It found the printer and all was successful.

Thanks again.. At last I have a scanner working under Ubuntu!

---

### Post by Locke_99GS on 2010-12-29
> **colinmccubbin said:**
> My question is 'why do you say python-dev is needed when the failure refers to python-devel'?

I'm glad it worked for you. 

*.dev and *-devel are different nomenclatures for the same thing, referring to development packages. RPM based distro's tend to refer to them as *-devel, while Debian based distro's refer to them as *-dev.

---

### Post by nealaustin on 2011-02-28
Went out and bought a HP Photoscan D110 today. Downloaded and installed the from HP site: "hplip-3.11.1.run" and saved the very simple instructions to my Ubuntu 10.04 32bit netbook (system76) and then copied the file via thumb drive to my wife's Ubuntu 10.04 64bit desktop machine and installed it there. SimpleScan works!, printing works! Wireless works! Awesome printer indeed. :popcorn: I first tried to use a similar printer to set it up but the scanner didn't work. I am by no means an expert, but reading this forum before I bought this printer guided me to the right product for Linux. Thanks everyone!

---

