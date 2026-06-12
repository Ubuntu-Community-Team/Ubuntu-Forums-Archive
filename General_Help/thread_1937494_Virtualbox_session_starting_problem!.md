---
title: "Virtualbox session starting problem!"
date: 2012-03-07
forum: General Help
---

### Post by Panxo on 2012-03-07
Hi there again.

My current operative system is ubuntu 11.10. Also, I'm using Oracle Virtualbox 4.1.2 with windows 7 as guest. Lately I could launch it without any problem, but now any time I try to start up win 7 it tells this:

[img]http://img442.imageshack.us/img442/2366/virtualboxerror.png[/img]

I've already tried reinstalling it like 3 times, but nothing seems to work. Last thing I tried to do on virtualbox was to install the extension package, but it didn't work as well. Later I was trying to install nvidia drivers on ubuntu in order to play games with win 7 (trying to load direct3d but it crashes with openLG). Unfortunately, I don't remember last thing I did on the terminal, but after that it didn't want to start again.

Any suggestions?

---

### Post by lechien73 on 2012-03-08
Hi & thanks for the screenshot,

First, make sure that you don't have saved sessions for any VM.

Secondly, open a terminal window and try the following commands to replace the extension packs:

```
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms
```

Thirdly, check under USB support and try disabling **Enable USB 2.0 (ECHI) Controller**

---

### Post by Panxo on 2012-03-08
Ok, I put the two commands you said, but the problem remains the same. 

Here's what I've got:

1) sudo apt-get remove virtualbox-dkms

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox-dkms is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
pango@Panxo:~$ clear

pango@Panxo:~$ sudo apt-get autoremove virtualbox
sudo: unable to resolve host Panxo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  virtualbox virtualbox-qt
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 63.8 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 178724 files and directories currently installed.)
Removing virtualbox-qt ...
Removing virtualbox ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot

```

2) sudo apt-get install virtualbox-dkms

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  virtualbox virtualbox-qt
Suggested packages:
  vde2
The following NEW packages will be installed:
  virtualbox virtualbox-dkms virtualbox-qt
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.7 MB of archives.
After this operation, 68.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe virtualbox amd64 4.1.2-dfsg-1ubuntu1 [15.6 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe virtualbox-dkms all 4.1.2-dfsg-1ubuntu1 [665 kB]                               
Get:3 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe virtualbox-qt amd64 4.1.2-dfsg-1ubuntu1 [6,369 kB]                             
Fetched 22.7 MB in 1min 44s (218 kB/s)                                                                                                     
Selecting previously deselected package virtualbox.
(Reading database ... 178451 files and directories currently installed.)
Unpacking virtualbox (from .../virtualbox_4.1.2-dfsg-1ubuntu1_amd64.deb) ...
Selecting previously deselected package virtualbox-dkms.
Unpacking virtualbox-dkms (from .../virtualbox-dkms_4.1.2-dfsg-1ubuntu1_all.deb) ...
Selecting previously deselected package virtualbox-qt.
Unpacking virtualbox-qt (from .../virtualbox-qt_4.1.2-dfsg-1ubuntu1_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for shared-mime-info ...
Processing triggers for hicolor-icon-theme ...
Setting up virtualbox (4.1.2-dfsg-1ubuntu1) ...
 * Stopping VirtualBox kernel modules                                                                                                [ OK ] 
 * Starting VirtualBox kernel modules                                                                                                        * No suitable module for running kernel found
                                                                                                                                     [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.
Processing triggers for python-central ...
Setting up virtualbox-dkms (4.1.2-dfsg-1ubuntu1) ...
Loading new virtualbox-4.1.2 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-16-generic
Building initial module for 3.0.0-16-generic
Done.

vboxdrv:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-16-generic/updates/dkms/

vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-16-generic/updates/dkms/

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-16-generic/updates/dkms/

vboxpci.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-16-generic/updates/dkms/

depmod.........

DKMS: install Completed.
 * Stopping VirtualBox kernel modules                                                                                                [ OK ] 
 * Starting VirtualBox kernel modules                                                                                                [ OK ] 
Setting up virtualbox-qt (4.1.2-dfsg-1ubuntu1) ...
```

---

### Post by Sergius14 on 2012-03-08
I think that sometime you added and installed the Guest Addionts (Extension Pack) and now for some reason you have removed it.


Try to add the extension pack (Oracle proprietary).


From File -> Preferences -> Extensions you can add them.


I personally prefer to download everything from [https://www.virtualbox.org/](https://www.virtualbox.org/) with extension pack and install manually. It is my personal like. Specially because apt has always old versions (right now, 4.1.8 is the latest, with many improvements in the additions and Windows 7 directx support).


The oracle extensions pack is free for non-commercial usage.

[URL="https://www.virtualbox.org/wiki/Downloads"]
https://www.virtualbox.org/wiki/Downloads[/URL]

---

### Post by Panxo on 2012-03-08
Couldn't do it! 

I downloaded it from where you said, but when I try to install the package, Vbox shows me this:

[img]http://img24.imageshack.us/img24/7918/extensionfailled.png[/img]

---

### Post by Sergius14 on 2012-03-08
Easy: you downloaded extension pack for 4.0 instead of 4.1


Download the extension tools for 4.1.2 or better, upgrade you VirtualBox to 4.1.8 and extension tools with 4.1 too with debs from that official web.

Uninstall previus packages from apt-get, although I guess that it may upgrade or uninstall the same software update.

---

### Post by Panxo on 2012-03-08
Alright!

Now it's starting! Thanks everyone again, problem solved!

---

