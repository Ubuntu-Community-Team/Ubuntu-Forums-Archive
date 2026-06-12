---
title: "update-manager won't open, deb installs fail"
date: 2009-08-14
forum: General Help
---

### Post by moorsey on 2009-08-14
Fresh 9.04 install, seemed to have this problem before I installed any updates etc, but can't confirm that. Red "stop" type sign appeared in the notification area (this is update-notifier). Hovering over the icon displays "an error occurred when checking for updates", Googling this brings up nothing useful.

Other symptoms are update-manager failing to open, nothing happens when clicking on it in the menu.

Also, seemingly related is the install of a few .deb files. Instead of bringing up the usual deb installer, nothing happens when opening .deb files. But running dpkg or apt-get install from terminal works fine.

Any thought's??  The only thing that is different between this install and other 9.04 installs is that this one is running software RAID.

Cheers

---

### Post by KhurramM on 2009-08-14
r u able to use apt-get, synaptic?

---

### Post by moorsey on 2009-08-14
do you mean can I run:

```
apt-get install synaptic
```

this tells me that I have the latest version installed, sorry if I mis-understood

---

### Post by Bucky Ball on 2009-08-14
```
sudo apt-get update

sudo apt-get upgrade

sudo apt-get autoremove
```Do they work in a terminal?

---

### Post by moorsey on 2009-08-14
yes, they work fine

well, I may have made the problem worse.  I did

```
apt-get remove update-manager
```

thinking a re-install of the package would help, but now it won't go on

the related packages ubuntu-desktop and update-notifier all seem to depend on each other, but they are left "unconfigured".  Not sure how I can configure them

---

### Post by moorsey on 2009-08-15
well, all now seems to be solved, a reboot sorted the configuration issues I mentioned in my last post.  Update manager now runs and packages install as they should.  No idea what caused the issue in the first place.  No updates have come through automatically yet, but everything seems as it should

Thanks for the replies guys

---

### Post by moorsey on 2009-08-15
ah, spoke too soon, not working now, was fine yesterday, but after another reboot, it is broken again.  Can't open update-manager and install deb packages.  Also can't "Edit Menus" for some reason

---

### Post by Soul-Sing on 2009-08-15
```
sudo apt-get update
```? Does this work? Any errors?

---

### Post by Soul-Sing on 2009-08-15
```
sudo apt-get update
```? Does this work? Any errors?

---

### Post by moorsey on 2009-08-15
yup, apt-get commands still working, it still fails on the update-manager --configure though, those 3 packages I mentioned don't seem to be install properly, but removing or installing any of them throws up configure or dependency errors

---

### Post by Bucky Ball on 2009-08-15
> **leoquant said:**
> ```
sudo apt-get update
```? Does this work? Any errors?

Read previous posts. This question has been asked and answered already. :)

---

### Post by moorsey on 2009-08-24
still having issues with this.  Is there a way I can just replace all the original packages that come with 9.04?  A repair type setup?

This issue is stopping me from running most applications on this system, Firefox and Terminal work, but most other stuff fails due to the update-manager not configuring properly

---

### Post by Bucky Ball on 2009-08-24
You might get some relief here:

[http://ubuntuforums.org/showthread.php?p=4952791](http://ubuntuforums.org/showthread.php?p=4952791)

Solutions start at post #9. Good luck.

---

### Post by moorsey on 2009-09-01
Hi there, back on this problem, tried a million and one things, below is the output from an "apt-get update" and "apt-get upgrade", maybe this will twig with someone who has had similar problems!

```
airc@server146:~$ sudo apt-get update
[sudo] password for airc: 
Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_GB
Hit http://gb.archive.ubuntu.com jaunty Release.gpg
Hit http://gb.archive.ubuntu.com jaunty/main Translation-en_GB
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_GB
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_GB
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com jaunty-security Release
Hit http://gb.archive.ubuntu.com jaunty/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com jaunty/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com jaunty/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://gb.archive.ubuntu.com jaunty-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com jaunty-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com jaunty-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com jaunty-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com jaunty Release
Hit http://gb.archive.ubuntu.com jaunty-updates Release
Hit http://security.ubuntu.com jaunty-security/main Packages        
Hit http://gb.archive.ubuntu.com jaunty/main Packages               
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty/restricted Packages
Hit http://gb.archive.ubuntu.com jaunty/main Sources
Hit http://gb.archive.ubuntu.com jaunty/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty/universe Packages
Hit http://gb.archive.ubuntu.com jaunty/universe Sources
Hit http://gb.archive.ubuntu.com jaunty/multiverse Packages
Hit http://gb.archive.ubuntu.com jaunty/multiverse Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/main Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/main Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Reading package lists... Done
airc@server146:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  python-gobject
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/1091kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 161465 files and directories currently installed.)
Preparing to replace python-gobject 2.16.1-1ubuntu2 (using .../python-gobject_2.16.1-1ubuntu3_i386.deb) ...
Illegal instruction
dpkg: warning - old pre-removal script returned error exit status 132
dpkg - trying script from the new package instead ...
Illegal instruction
dpkg: error processing /var/cache/apt/archives/python-gobject_2.16.1-1ubuntu3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 132
Illegal instruction
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 132
Preparing to replace update-manager 1:0.111.9 (using .../update-manager_1%3a0.111.9_all.deb) ...
Illegal instruction
dpkg: warning - old pre-removal script returned error exit status 132
dpkg - trying script from the new package instead ...
Illegal instruction
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.111.9_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 132
Illegal instruction
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 132
Errors were encountered while processing:
 /var/cache/apt/archives/python-gobject_2.16.1-1ubuntu3_i386.deb
 /var/cache/apt/archives/update-manager_1%3a0.111.9_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Output from "apt-get install update-manager"
```
airc@server146:~$ sudo apt-get install update-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B/1091kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 161465 files and directories currently installed.)
Preparing to replace python-gobject 2.16.1-1ubuntu2 (using .../python-gobject_2.16.1-1ubuntu2_i386.deb) ...
Illegal instruction
dpkg: warning - old pre-removal script returned error exit status 132
dpkg - trying script from the new package instead ...
Illegal instruction
dpkg: error processing /var/cache/apt/archives/python-gobject_2.16.1-1ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 132
Illegal instruction
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 132
Preparing to replace update-manager 1:0.111.9 (using .../update-manager_1%3a0.111.9_all.deb) ...
Illegal instruction
dpkg: warning - old pre-removal script returned error exit status 132
dpkg - trying script from the new package instead ...
Illegal instruction
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.111.9_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 132
Illegal instruction
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 132
Errors were encountered while processing:
 /var/cache/apt/archives/python-gobject_2.16.1-1ubuntu2_i386.deb
 /var/cache/apt/archives/update-manager_1%3a0.111.9_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by moorsey on 2009-09-01
just looking at the help for dpkg, ran "dpkg --audit".  Here is the output:

```
airc@server146:~$ sudo dpkg --audit
The following packages are in a mess due to serious problems during
installation. They must be reinstalled for them (and any packages
that depend on them) to function properly:
 python-gobject       Python bindings for the GObject library
 update-manager       GNOME application that manages apt updates

The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 samba                SMB/CIFS file, print, and login server for Unix
```

I just tried to install Samba, hence that as an extra.  It won't configure any new packages due to this issue

---

### Post by Bucky Ball on 2009-09-02
```
sudo apt-get autoremove
sudo apt-get remove python-gobject update-manager samba
```

Then reinstall what you need to.

Another way of doing this is going into Synaptic package manager and 'fix broken packages'. Along the bottom bar you get a read out; it shows there if you have any broken packages. Synaptic will do its level best but you might need to go the terminal.

---

### Post by moorsey on 2009-09-02
thanks for your continued help.

I tried to do an uninstall on update-manager previously, with no luck.  But ran the two commands suggested, no luck though, nothing seems to want to remove or install:

```
airc@server146:~$ sudo apt-get autoremove
[sudo] password for airc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
3 not fully installed or removed.
Need to get 0B/1091kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 161529 files and directories currently installed.)
Preparing to replace python-gobject 2.16.1-1ubuntu2 (using .../python-gobject_2.16.1-1ubuntu2_i386.deb) ...
Illegal instruction
dpkg: warning - old pre-removal script returned error exit status 132
dpkg - trying script from the new package instead ...
Illegal instruction
dpkg: error processing /var/cache/apt/archives/python-gobject_2.16.1-1ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 132
Illegal instruction
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 132
Preparing to replace update-manager 1:0.111.9 (using .../update-manager_1%3a0.111.9_all.deb) ...
Illegal instruction
dpkg: warning - old pre-removal script returned error exit status 132
dpkg - trying script from the new package instead ...
Illegal instruction
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.111.9_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 132
Illegal instruction
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 132
Errors were encountered while processing:
 /var/cache/apt/archives/python-gobject_2.16.1-1ubuntu2_i386.deb
 /var/cache/apt/archives/update-manager_1%3a0.111.9_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
airc@server146:~$ sudo apt-get remove python-gobject update-manager samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  alacarte apport-gtk apturl checkbox-gtk computer-janitor-gtk
  fast-user-switch-applet gdebi gedit gimp gnome-about gnome-app-install
  gnome-applets gnome-codec-install gnome-control-center gnome-games
  gnome-menus gnome-orca gnome-panel gnome-session hal-cups-utils
  indicator-applet indicator-messages jockey-gtk language-selector nautilus
  nautilus-dropbox nautilus-share onboard python-glade2 python-gmenu
  python-gnome2 python-gnome2-desktop python-gobject python-gst0.10
  python-gtk2 python-gtkhtml2 python-gtksourceview2 python-notify
  python-pyatspi python-sexy python-vte rhythmbox samba
  software-properties-gtk system-config-printer-gnome totem totem-plugins
  ubufox update-manager update-notifier usb-creator
0 upgraded, 0 newly installed, 51 to remove and 1 not upgraded.
3 not fully installed or removed.
After this operation, 93.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 161528 files and directories currently installed.)
Removing system-config-printer-gnome ...
Illegal instruction
dpkg: error processing system-config-printer-gnome (--remove):
 subprocess pre-removal script returned error exit status 132
Illegal instruction
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 132
Removing gnome-applets ...
Illegal instruction
dpkg: error processing gnome-applets (--remove):
 subprocess post-removal script returned error exit status 132
Removing fast-user-switch-applet ...
Illegal instruction
dpkg: error processing fast-user-switch-applet (--remove):
 subprocess pre-removal script returned error exit status 132
Removing ubufox ...
Removing apturl ...
Illegal instruction
dpkg: error processing apturl (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing totem ...
Removing totem-plugins ...
Illegal instruction
dpkg: error processing totem-plugins (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing gedit ...
Illegal instruction
dpkg: error processing gedit (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing python-gtksourceview2 ...
Illegal instruction
dpkg: error processing python-gtksourceview2 (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing nautilus-dropbox ...
Removing language-selector ...
Illegal instruction
dpkg: error processing language-selector (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing gnome-app-install ...
Illegal instruction
dpkg: error processing gnome-app-install (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing checkbox-gtk ...
Illegal instruction
dpkg: error processing checkbox-gtk (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing apport-gtk ...
Removing usb-creator ...
Illegal instruction
dpkg: error processing usb-creator (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing software-properties-gtk ...
Illegal instruction
dpkg: error processing software-properties-gtk (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing rhythmbox ...
Illegal instruction
dpkg: error processing rhythmbox (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing update-notifier ...
Illegal instruction
dpkg: error processing update-notifier (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              dpkg: error processing update-manager (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
No apport report written because MaxReports is reached already
                                                              Removing gdebi ...
Illegal instruction
dpkg: error processing gdebi (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing python-vte ...
Illegal instruction
dpkg: error processing python-vte (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing python-sexy ...
Removing jockey-gtk ...
Removing python-notify ...
Illegal instruction
dpkg: error processing python-notify (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing python-gtkhtml2 ...
Illegal instruction
dpkg: error processing python-gtkhtml2 (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing gnome-orca ...
Illegal instruction
dpkg: error processing gnome-orca (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing python-gnome2-desktop ...
Illegal instruction
dpkg: error processing python-gnome2-desktop (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing python-pyatspi ...
Illegal instruction
dpkg: error processing python-pyatspi (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing nautilus-share ...
Removing nautilus ...
Removing gnome-session ...
Illegal instruction
dpkg: error processing gnome-session (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing alacarte ...
Illegal instruction
dpkg: error processing alacarte (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing onboard ...
Illegal instruction
dpkg: error processing onboard (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing computer-janitor-gtk ...
Removing gnome-games ...
Removing gnome-codec-install ...
Illegal instruction
dpkg: error processing gnome-codec-install (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing gimp ...
Illegal instruction
dpkg: error processing gimp (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing python-gst0.10 ...
Illegal instruction
dpkg: error processing python-gst0.10 (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing hal-cups-utils ...
Removing samba ...
Removing indicator-applet ...
Illegal instruction
dpkg: error processing indicator-applet (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing indicator-messages ...
Removing gnome-panel ...
Removing gnome-about ...
Removing python-gnome2 ...
Illegal instruction
dpkg: error processing python-gnome2 (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing gnome-control-center ...
Removing gnome-menus ...
Illegal instruction
dpkg: error processing gnome-menus (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing python-gmenu ...
Illegal instruction
dpkg: error processing python-gmenu (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing python-glade2 ...
Illegal instruction
dpkg: error processing python-glade2 (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              Removing python-gtk2 ...
Illegal instruction
dpkg: error processing python-gtk2 (--remove):
 subprocess pre-removal script returned error exit status 132
No apport report written because MaxReports is reached already
                                                              dpkg: error processing python-gobject (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Processing triggers for man-db ...
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
 * Restarting Hardware abstraction layer hald                            [ OK ] 
Processing triggers for ufw ...
Illegal instruction
Processing ufw triggers failed. Ignoring.
Errors were encountered while processing:
 system-config-printer-gnome
 gnome-applets
 fast-user-switch-applet
 apturl
 totem-plugins
 gedit
 python-gtksourceview2
 language-selector
 gnome-app-install
 checkbox-gtk
 usb-creator
 software-properties-gtk
 rhythmbox
 update-notifier
 update-manager
 gdebi
 python-vte
 python-notify
 python-gtkhtml2
 gnome-orca
 python-gnome2-desktop
 python-pyatspi
 gnome-session
 alacarte
 onboard
 gnome-codec-install
 gimp
 python-gst0.10
 indicator-applet
 python-gnome2
 gnome-menus
 python-gmenu
 python-glade2
 python-gtk2
 python-gobject
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bucky Ball on 2009-09-02
Have you tried fixing broken packages through Synaptic Package Manager?

---

### Post by moorsey on 2009-09-02
ooops, sorry, meant to put that in previous post!  Yes, tried that fix broken packages, it doesn't show any messages or similar, so assume it does something, just not sure what, no output.

Also tried removing and installing packages via Synaptic, but no further luck there

Cheers!

---

### Post by oldos2er on 2009-09-02
Have you tried **sudo apt-get clean **?

---

### Post by moorsey on 2009-09-03
thanks.  Tried the clean option, didn't give any output, but did seem to do something, ran an update and upgrade after that, looks like the same errors:

```
airc@server146:~$ sudo apt-get clean
[sudo] password for airc:
airc@server146:~$ sudo apt-get update
Hit http://gb.archive.ubuntu.com jaunty Release.gpg
Get: 1 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Hit http://security.ubuntu.com jaunty-security Release.gpg  
Ign http://security.ubuntu.com jaunty-security/main Translation-en_GB
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_GB
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_GB
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com jaunty-security Release      
Hit http://security.ubuntu.com jaunty-security/main Packages  
Get: 2 http://gb.archive.ubuntu.com jaunty/restricted Translation-en_GB [4640B]
Get: 3 http://gb.archive.ubuntu.com jaunty/universe Translation-en_GB [35.2kB]
Hit http://security.ubuntu.com jaunty-security/restricted Packages            
Hit http://security.ubuntu.com jaunty-security/main Sources    
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Get: 4 http://gb.archive.ubuntu.com jaunty/multiverse Translation-en_GB [47.5kB]
Hit http://gb.archive.ubuntu.com jaunty-updates Release.gpg                   
Ign http://gb.archive.ubuntu.com jaunty-updates/main Translation-en_GB      
Ign http://gb.archive.ubuntu.com jaunty-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com jaunty-updates/universe Translation-en_GB  
Ign http://gb.archive.ubuntu.com jaunty-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com jaunty Release                             
Hit http://security.ubuntu.com jaunty-security/universe Sources             
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://gb.archive.ubuntu.com jaunty-updates Release                    
Hit http://gb.archive.ubuntu.com jaunty/main Packages                         
Hit http://gb.archive.ubuntu.com jaunty/restricted Packages
Hit http://gb.archive.ubuntu.com jaunty/main Sources
Hit http://gb.archive.ubuntu.com jaunty/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty/universe Packages
Hit http://gb.archive.ubuntu.com jaunty/universe Sources
Hit http://gb.archive.ubuntu.com jaunty/multiverse Packages
Hit http://gb.archive.ubuntu.com jaunty/multiverse Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/main Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/main Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Sources
Fetched 140kB in 0s (159kB/s)
Reading package lists... Done
airc@server146:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree      
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  fast-user-switch-applet: Depends: gnome-panel but it is not installed
  gnome-app-install: Depends: python-sexy but it is not installed
  gnome-applets: Depends: gnome-panel (>= 2.13.4) but it is not installed
  gnome-session: Depends: gnome-control-center (>= 1:2.22) but it is not installed
                 Recommends: gnome-panel but it is not installed
                 Recommends: nautilus but it is not installed
  indicator-applet: Depends: gnome-panel but it is not installed
                    Depends: indicator-messages but it is not installed
E: Unmet dependencies. Try using -f.
airc@server146:~$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Correcting dependencies...Done
The following NEW packages will be installed
  gnome-about gnome-control-center gnome-panel indicator-messages python-sexy
The following packages will be upgraded:
  dnsmasq-base python-gobject
2 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
35 not fully installed or removed.
Need to get 2514kB of archives.
After this operation, 3158kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com jaunty-updates/main python-gobject 2.16.1-1ubuntu3 [318kB]
Get: 2 http://gb.archive.ubuntu.com jaunty/main gnome-control-center 1:2.26.0-0ubuntu3 [403kB]
Get: 3 http://gb.archive.ubuntu.com jaunty-updates/main gnome-about 1:2.26.1-0ubuntu2 [156kB]
Get: 4 http://gb.archive.ubuntu.com jaunty/main gnome-panel 1:2.26.0-0ubuntu7 [396kB]
Get: 5 http://gb.archive.ubuntu.com jaunty-updates/main gnome-applets 2.26.1-0ubuntu1 [188kB]
Get: 6 http://gb.archive.ubuntu.com jaunty/main python-sexy 0.1.9-1ubuntu2 [16.2kB]
Get: 7 http://gb.archive.ubuntu.com jaunty/main indicator-messages 0.1.6-0ubuntu1 [42.2kB]
Get: 8 http://gb.archive.ubuntu.com jaunty-updates/main update-manager 1:0.111.9 [773kB]
Get: 9 http://gb.archive.ubuntu.com jaunty-updates/main dnsmasq-base 2.47-3ubuntu0.1 [222kB]
Fetched 2514kB in 6s (373kB/s)                                                
Preconfiguring packages ...
Selecting previously deselected package python-gobject.
(Reading database ... 161125 files and directories currently installed.)
Preparing to replace python-gobject 2.16.1-1ubuntu2 (using .../python-gobject_2.16.1-1ubuntu3_i386.deb) ...
Illegal instruction
dpkg: warning - old pre-removal script returned error exit status 132
dpkg - trying script from the new package instead ...
Illegal instruction
dpkg: error processing /var/cache/apt/archives/python-gobject_2.16.1-1ubuntu3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 132
Illegal instruction
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 132
Selecting previously deselected package gnome-control-center.
Unpacking gnome-control-center (from .../gnome-control-center_1%3a2.26.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package gnome-about.
Unpacking gnome-about (from .../gnome-about_1%3a2.26.1-0ubuntu2_all.deb) ...
Selecting previously deselected package gnome-panel.
Unpacking gnome-panel (from .../gnome-panel_1%3a2.26.0-0ubuntu7_i386.deb) ...
Selecting previously deselected package gnome-applets.
Preparing to replace gnome-applets 2.26.1-0ubuntu1 (using .../gnome-applets_2.26.1-0ubuntu1_i386.deb) ...
Unpacking replacement gnome-applets ...
Illegal instruction
dpkg: warning - old post-removal script returned error exit status 132
dpkg - trying script from the new package instead ...
Illegal instruction
dpkg: error processing /var/cache/apt/archives/gnome-applets_2.26.1-0ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 132
Illegal instruction
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 132
Selecting previously deselected package python-sexy.
Unpacking python-sexy (from .../python-sexy_0.1.9-1ubuntu2_i386.deb) ...
Selecting previously deselected package indicator-messages.
Unpacking indicator-messages (from .../indicator-messages_0.1.6-0ubuntu1_i386.deb) ...
Selecting previously deselected package update-manager.
Preparing to replace update-manager 1:0.111.9 (using .../update-manager_1%3a0.111.9_all.deb) ...
Illegal instruction
dpkg: warning - old pre-removal script returned error exit status 132
dpkg - trying script from the new package instead ...
Illegal instruction
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.111.9_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 132
Illegal instruction
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 132
Preparing to replace dnsmasq-base 2.47-3 (using .../dnsmasq-base_2.47-3ubuntu0.1_i386.deb) ...
Unpacking replacement dnsmasq-base ...
Processing triggers for man-db ...
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/python-gobject_2.16.1-1ubuntu3_i386.deb
 /var/cache/apt/archives/gnome-applets_2.26.1-0ubuntu1_i386.deb
 /var/cache/apt/archives/update-manager_1%3a0.111.9_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Also tried an install of just update manager
```
airc@server146:~$ sudo apt-get install update-manager
Reading package lists... Done
Building dependency tree      
Reading state information... Done
update-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
41 not fully installed or removed.
Need to get 318kB/1278kB of archives.
After this operation, 0B of additional disk space will be used.
Get: 1 http://gb.archive.ubuntu.com jaunty/main python-gobject 2.16.1-1ubuntu2 [318kB]
Fetched 318kB in 2s (155kB/s)         
Preconfiguring packages ...
(Reading database ... 161243 files and directories currently installed.)
Preparing to replace python-gobject 2.16.1-1ubuntu2 (using .../python-gobject_2.16.1-1ubuntu2_i386.deb) ...
Illegal instruction
dpkg: warning - old pre-removal script returned error exit status 132
dpkg - trying script from the new package instead ...
Illegal instruction
dpkg: error processing /var/cache/apt/archives/python-gobject_2.16.1-1ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 132
Illegal instruction
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 132
Preparing to replace gnome-applets 2.26.1-0ubuntu1 (using .../gnome-applets_2.26.1-0ubuntu1_i386.deb) ...
Unpacking replacement gnome-applets ...
Illegal instruction
dpkg: warning - old post-removal script returned error exit status 132
dpkg - trying script from the new package instead ...
Illegal instruction
dpkg: error processing /var/cache/apt/archives/gnome-applets_2.26.1-0ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 132
Illegal instruction
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 132
Preparing to replace update-manager 1:0.111.9 (using .../update-manager_1%3a0.111.9_all.deb) ...
Illegal instruction
dpkg: warning - old pre-removal script returned error exit status 132
dpkg - trying script from the new package instead ...
Illegal instruction
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.111.9_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 132
Illegal instruction
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 132
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/python-gobject_2.16.1-1ubuntu2_i386.deb
 /var/cache/apt/archives/gnome-applets_2.26.1-0ubuntu1_i386.deb
 /var/cache/apt/archives/update-manager_1%3a0.111.9_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
airc@se
```

---

### Post by Bucky Ball on 2009-09-03
Have you also tried:

```
sudo apt-get -f install
```From your output:

```
Reading package lists... Done
airc@server146:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree      
Reading state information... Done
**You might want to run &#8216;apt-get -f install&#8217; to correct these.**

```Sorry if you have tried that in an earlier post.

The order should be update *then* upgrade. ;-)

---

### Post by moorsey on 2009-09-03
hey, just gave that a try, but same results again I'm afraid

---

### Post by moorsey on 2009-09-03
sorry, ignore last message, I was reading the wrong page of posts, will try latest suggestion now....

---

### Post by moorsey on 2009-09-03
ok, I had tried the -f switch on an upgrade command, not with individual packages.

When I try it on update-manager, the output says that it is already at the current version, so whatever is telling update-manager what is installed and what is not, must be corrupt or similar

Looking around the forums it would seem that this file (can't remember what it is called) cannot be "re-built"

Looking more and more like a re-build from scratch, I do hope not though

---

