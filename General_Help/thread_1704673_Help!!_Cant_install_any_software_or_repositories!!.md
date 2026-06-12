---
title: "Help!! Cant install any software or repositories???!!"
date: 2011-03-11
forum: General Help
---

### Post by jamiegrant01 on 2011-03-11
I try to install the detdeb repo, i get this error.. 
Only one software management tool is allowed to run at the same time
please close the other application e.g. 'update manager', 'aptitude' or 'synaptic' first.

i have none of those open.

it was working completely fine before i installled the medibuntu and get deb repos... im completely new to ubuntu and linux. the only linux i know is from hacking my wii which is basically nothing.

then when i try to install ANY software, i get this error.

Previous installation hasn't been completed

The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software.

WTF?!?!?!? HELP!?!

---

### Post by dabomb1022 on 2011-03-11
Open the terminal and try sudo apt-get -f install. and maybe sudo apt-get autoremove if prompted to.  Btw, have you tried rebooting?

---

### Post by jamiegrant01 on 2011-03-11
I did, and i got some wierd microsoft crap..

Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring ttf-mscorefonts-installer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; TrueType core fonts for the Web EULA                                      &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                         &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement       &#9618; 
 &#9474; ("EULA") is a legal agreement between you (either an individual or a      &#9618; 
 &#9474; single entity) and Microsoft Corporation for the Microsoft software       &#9618; 
 &#9474; accompanying this EULA, which includes computer software and may include  &#9618; 
 &#9474; associated media, printed materials, and "on-line" or electronic          &#9618; 
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your      &#9618; 
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be    &#9618; 
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of      &#9618; 
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                          &#9618; 
 &#9474;                                                                           &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                                                           &#9474; 



makes no sense to me.
yes i restarted my computer and that didnt work.
this is what happened with the first command you gave me
jamie@jamie-desktop:~$ sudo apt-get -f install
[sudo] password for jamie: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jamie@jamie-desktop:~$ 

what the hell....................................................:(

 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;

---

### Post by krishna1650 on 2011-03-11
> **jamiegrant01 said:**
> I did, and i got some wierd microsoft crap..

Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring ttf-mscorefonts-installer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; TrueType core fonts for the Web EULA                                      &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                         &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement       &#9618; 
 &#9474; ("EULA") is a legal agreement between you (either an individual or a      &#9618; 
 &#9474; single entity) and Microsoft Corporation for the Microsoft software       &#9618; 
 &#9474; accompanying this EULA, which includes computer software and may include  &#9618; 
 &#9474; associated media, printed materials, and "on-line" or electronic          &#9618; 
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your      &#9618; 
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be    &#9618; 
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of      &#9618; 
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                          &#9618; 
 &#9474;                                                                           &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                                                           &#9474; 



makes no sense to me.
yes i restarted my computer and that didnt work.
this is what happened with the first command you gave me
jamie@jamie-desktop:~$ sudo apt-get -f install
[sudo] password for jamie: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jamie@jamie-desktop:~$ 

what the hell....................................................:(

 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;

Try to kill any running synaptic or dpkg processes.

---

### Post by jamiegrant01 on 2011-03-11
How?

---

### Post by jamiegrant01 on 2011-03-11
PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 cpuset
   12 ?        00:00:00 khelper
   13 ?        00:00:00 netns
   14 ?        00:00:00 async/mgr
   15 ?        00:00:00 pm
   17 ?        00:00:00 sync_supers
   18 ?        00:00:00 bdi-default
   19 ?        00:00:00 kintegrityd/0
   20 ?        00:00:00 kintegrityd/1
   21 ?        00:00:00 kblockd/0
   22 ?        00:00:00 kblockd/1
   23 ?        00:00:00 kacpid
   24 ?        00:00:00 kacpi_notify
   25 ?        00:00:00 kacpi_hotplug
   26 ?        00:00:00 ata/0
   27 ?        00:00:00 ata/1
   28 ?        00:00:00 ata_aux
   29 ?        00:00:00 ksuspend_usbd
   30 ?        00:00:00 khubd
   31 ?        00:00:00 kseriod
   32 ?        00:00:00 kmmcd
   35 ?        00:00:00 khungtaskd
   36 ?        00:00:00 kswapd0
   37 ?        00:00:00 ksmd
   38 ?        00:00:00 aio/0
   39 ?        00:00:00 aio/1
   40 ?        00:00:00 ecryptfs-kthrea
   41 ?        00:00:00 crypto/0
   42 ?        00:00:00 crypto/1
   46 ?        00:00:00 kstriped
   47 ?        00:00:00 kmpathd/0
   48 ?        00:00:00 kmpathd/1
   49 ?        00:00:00 kmpath_handlerd
   50 ?        00:00:00 ksnapd
   51 ?        00:00:00 kondemand/0
   52 ?        00:00:00 kondemand/1
   53 ?        00:00:00 kconservative/0
   54 ?        00:00:00 kconservative/1
  241 ?        00:00:00 scsi_eh_0
  245 ?        00:00:00 scsi_eh_1
  248 ?        00:00:00 scsi_eh_2
  249 ?        00:00:00 usb-storage
  252 ?        00:00:00 scsi_eh_3
  253 ?        00:00:00 usb-storage
  256 ?        00:00:00 scsi_eh_4
  257 ?        00:00:00 scsi_eh_5
  276 ?        00:00:00 kjournald
  309 ?        00:00:00 flush-8:0
  342 ?        00:00:00 upstart-udev-br
  344 ?        00:00:00 udevd
  497 ?        00:00:00 udevd
  498 ?        00:00:00 udevd
  592 ?        00:00:00 kpsmoused
  700 ?        00:00:14 phy0
  736 ?        00:00:00 hd-audio0
  788 ?        00:00:00 rsyslogd
  804 ?        00:00:00 dbus-daemon
  825 ?        00:00:00 avahi-daemon
  829 ?        00:00:00 avahi-daemon
  831 ?        00:00:00 NetworkManager
  833 ?        00:00:00 modem-manager
  862 ?        00:00:00 wpa_supplicant
  873 tty4     00:00:00 getty
  877 tty5     00:00:00 getty
  885 tty2     00:00:00 getty
  886 tty3     00:00:00 getty
  890 tty6     00:00:00 getty
  892 ?        00:00:00 irqbalance
  893 ?        00:00:00 acpid
  906 ?        00:00:00 cron
  907 ?        00:00:00 atd
  957 ?        00:00:00 cupsd
 1060 tty1     00:00:00 getty
 1071 ?        00:00:00 gdm-binary
 1080 ?        00:00:00 console-kit-dae
 1146 ?        00:00:00 gdm-simple-slav
 1149 tty7     00:01:08 Xorg
 1159 ?        00:00:00 gdm-session-wor
 1168 ?        00:00:00 gnome-session
 1212 ?        00:00:00 seahorse-agent
 1215 ?        00:00:00 dbus-launch
 1216 ?        00:00:00 dbus-daemon
 1219 ?        00:00:01 gconfd-2
 1225 ?        00:00:00 gnome-keyring-d
 1226 ?        00:00:01 gnome-settings-
 1231 ?        00:00:00 gvfsd
 1234 ?        00:00:22 compiz
 1235 ?        00:00:02 gnome-panel
 1241 ?        00:00:00 nautilus
 1243 ?        00:00:00 gnome-power-man
 1245 ?        00:00:00 trackerd
 1246 ?        00:00:00 gvfs-fuse-daemo
 1249 ?        00:00:00 nm-applet
 1254 ?        00:00:00 bluetooth-apple
 1256 ?        00:00:01 polkit-gnome-au
 1259 ?        00:00:00 pulseaudio
 1261 ?        00:00:00 tracker-applet
 1264 ?        00:00:00 rtkit-daemon
 1268 ?        00:00:00 hald
 1273 ?        00:00:00 polkitd
 1275 ?        00:00:00 hald-runner
 1279 ?        00:00:00 upowerd
 1300 ?        00:00:00 bonobo-activati
 1307 ?        00:00:00 gvfsd-trash
 1334 ?        00:00:00 gconf-helper
 1369 ?        00:00:00 gvfs-gdu-volume
 1370 ?        00:00:02 wnck-applet
 1371 ?        00:00:00 trashapplet
 1374 ?        00:00:00 udisks-daemon
 1375 ?        00:00:00 udisks-daemon
 1376 ?        00:00:00 hald-addon-inpu
 1382 ?        00:00:00 hald-addon-rfki
 1390 ?        00:00:00 hald-addon-stor
 1392 ?        00:00:00 hald-addon-stor
 1393 ?        00:00:00 hald-addon-stor
 1394 ?        00:00:00 hald-addon-stor
 1395 ?        00:00:00 hald-addon-stor
 1400 ?        00:00:00 hald-addon-cpuf
 1401 ?        00:00:00 hald-addon-acpi
 1404 ?        00:00:00 hald-addon-stor
 1406 ?        00:00:00 gvfs-gphoto2-vo
 1409 ?        00:00:00 gvfs-afc-volume
 1412 ?        00:00:00 tracker-indexer
 1429 ?        00:00:00 indicator-apple
 1430 ?        00:00:00 clock-applet
 1433 ?        00:00:00 notification-ar
 1434 ?        00:00:00 indicator-apple
 1442 ?        00:00:00 gvfsd-burn
 1471 ?        00:00:00 gvfsd-metadata
 1477 ?        00:00:00 indicator-me-se
 1479 ?        00:00:00 indicator-sessi
 1482 ?        00:00:00 indicator-appli
 1484 ?        00:00:00 indicator-sound
 1486 ?        00:00:00 indicator-messa
 1487 ?        00:00:00 sh
 1488 ?        00:00:02 gtk-window-deco
 1497 ?        00:00:00 gnome-screensav
 1503 ?        00:00:00 gdu-notificatio
 1512 ?        00:00:00 dhclient
 1519 ?        00:00:00 notify-osd
 1577 ?        00:00:00 evolution-alarm
 1579 ?        00:00:00 python
 1585 ?        00:00:00 evolution-data-
 1589 ?        00:00:00 evolution-excha
 1613 ?        00:00:04 ubuntuone-syncd
 1627 ?        00:00:00 update-notifier
 1649 ?        00:00:00 firefox
 1654 ?        00:00:00 run-mozilla.sh
 1658 ?        00:01:43 firefox-bin
 1707 ?        00:00:00 gvfsd-http
 1723 ?        00:00:00 update-apt-xapi
 2619 ?        00:00:00 apt-get
 2637 pts/1    00:00:00 dpkg
 2644 pts/1    00:00:00 frontend
 2657 pts/1    00:00:00 preinst
 2659 pts/1    00:00:00 whiptail
 2702 ?        00:00:00 gnome-terminal
 2703 ?        00:00:00 gnome-pty-helpe
 2704 pts/2    00:00:00 bash
 2748 ?        00:00:00 system-service-
 2752 pts/2    00:00:00 ps
 

these are the running processes. which one do i kill and how do i do that?

---

### Post by krishna1650 on 2011-03-11
2619 ? 00:00:00 apt-get
2637 pts/1 00:00:00 dpkg

kill using command
$kill -9 <pid>

here pid=2619 and 2637.

---

### Post by dabomb1022 on 2011-03-11
The error is because some other thing is installing something. that is weird! Hopefully killing it will fix it.

---

### Post by jamiegrant01 on 2011-03-11
i tried, said not permitted. im going to smash my comp with a hammer.

---

### Post by krishna1650 on 2011-03-11
try with sudo (root)
command is
$sudo kill -9 <pid>

---

### Post by jamiegrant01 on 2011-03-11
when i restart my computer it doesnt have to dpkg still running, but still wont let me install anything. this might help..

jamie@jamie-desktop:~$ sudo dpkg --configure -a
[sudo] password for jamie: 
jamie@jamie-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  sdparm ethtool
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ttf-mscorefonts-installer
The following packages will be upgraded:
  ttf-mscorefonts-installer
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/40.2kB of archives.
After this operation, 221kB of additional disk space will be used.
Do you want to continue [Y/n]? 

i tried using apt-get autoremove, all it says after that is abort, same thing it says if i type n. when i type y, that thing in my second post is what comes up, and it wont let me click ok or do anything.

---

### Post by jamiegrant01 on 2011-03-11
then after it says abort, and no dpkg is running, when i try to install a program this is what happens.

package operation failed
the installation or removal of a software package failed

E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package. (due to missing arch): 

sad face

---

### Post by jamiegrant01 on 2011-03-11
wow. all i had to do was go to the update manager.. the ttf mscorefonts was in there, installed it from there with no problem and now i can install software. thanks for the help anyways.

---

### Post by krishna1650 on 2011-03-11
> **jamiegrant01 said:**
> then after it says abort, and no dpkg is running, when i try to install a program this is what happens.

package operation failed
the installation or removal of a software package failed

E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package. (due to missing arch): 

sad face

I also had same problem, installing package "ttf-mscorefonts-installer" or similar microsoft fonts package. Try to uninstall that package and update package list. This should fix the problem. At least that happened to me.

---

