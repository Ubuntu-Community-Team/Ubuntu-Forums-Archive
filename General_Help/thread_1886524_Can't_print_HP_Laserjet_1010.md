---
title: "Can't print HP Laserjet 1010"
date: 2011-11-25
forum: General Help
---

### Post by bookcrazy on 2011-11-25
I need some serious help with this.

I installed Ubuntu 10.04 on my work laptop and everything was going great (I could print over the network no problem) until I installed the Kubuntu and Edubuntu Desktop Environments as well to try and figure out what worked best. After playing around for a few days I decided to stick with Lucid and uninstalled Kubunutu and Edubuntu. I uninstalled Edubuntu by going into Synaptic Package Manager and selecting everything that came up with Edubuntu. No problems.

Then I uninstalled Kubuntu by typing in this code: ```
sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark cdrdao dolphin dragonplayer exiv2 foomatic-db-gutenprint freespacenotifier gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ibus-qt4 icoutils ijsgutenprint install-package jockey-kde k3b k3b-data kaddressbook kamera kate kbluetooth kcalc kcm-gtk kcm-touchpad kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-data kdebase-workspace kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdesudo kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knm-runtime knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete kopete-message-indicator korganizer kpackagekit kppp krdc krfb krosspython ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-debug-installer kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kubuntu-notification-helper kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libao2 libattica0 libaudio2 libboost-program-options1.40.0 libclucene0ldbl libdbusmenu-qt2 libepub0 libexiv2-6 libflac++6 libibus-qt1 libindicate-qt0 libiodbc2 libk3b6 libkcddb4 libkdcraw8 libkdecorations4 libkdepim4 libkephal4 libkexiv2-8 libkfontinst4 libkipi7 libkleo4 libkonq5 libkonq5-templates libkonqsidebarplugin4 libkopete4 libkpgp4 libkscreensaver5 libksgrd4 libksieve4 libksignalplotter4 libkwineffects1 libkworkspace4 liblastfm0 libmimelib4 libmng1 libmodplug0c2 libmpcdec3 libmsn0.3 libmysqlclient16 libokularcore1 libotr2 libpackagekit-glib2-12 libpackagekit-qt-12 libphonon4 libplasma-applet-system-monitor4 libplasma-geolocation-interface4 libplasma3 libplasmaclock4 libplasmagenericshell4 libpolkit-qt-1-0 libpoppler-qt4-3 libprocesscore4 libprocessui4 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libsolidcontrol4 libsolidcontrolifaces4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libtag-extras1 libtaskmanager4 libvncserver0 libweather-ion4 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-client-core-5.1 mysql-common mysql-server-core-5.1 network-manager-kde okular okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen oxygen-cursor-theme oxygen-icon-theme oxygen-icon-theme-complete packagekit packagekit-backend-apt phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-scriptengine-javascript plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel plasma-widget-kimpanel-backend-ibus plasma-widget-kubuntu-feedback plasma-widget-message-indicator plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace plymouth-theme-kubuntu-logo polkit-kde-1 printer-applet python-kde4 python-packagekit python-qt4 python-qt4-dbus python-sip quassel quassel-data shared-desktop-ontologies software-properties-kde soprano-daemon system-config-printer-kde systemsettings ttf-dejavu ttf-dejavu-extra update-manager-kde usb-creator-kde userconfig virtuoso-nepomuk && sudo apt-get install ubuntu-desktop
``` that I got from 

[http://www.psychocats.net/ubuntu/puregnomelucid](http://www.psychocats.net/ubuntu/puregnomelucid) (I'm not blaming anyone but myself, I just want to let people know why I entered the code I did). 

I really should have thought this one through better because now I can't print more than test pages. I have cups 1.4.3 installed on my computer but I can't really do anything with cups because I can't figure out what my username and password are for CUPS. 

When I go to System--->Administration--->Printing I can add the printer but then I can only print test pages. I am lost on what to do next. 

As for using HP Device Manager or HP Setup, I can't find my network printer so I can't install it that way. I would love to go to [www.linuxprinting.org](www.linuxprinting.org) and try that out but the website is down for maintenance. Really getting frustrated here!



Please give me a hand with this because I've read every forum post I can find and I just don't seem to be able to wrap my head around what to do. Thanks in advance fro any help anyone can give.

---

### Post by Sazhen86 on 2011-11-25
Hi.  I print to a couple of HP laserjet printers and I notice from the list of packages that you removed hpijs-pdds which is installed on my computer.  I'm not sure if it's going to help you, but I thought I'd point it out just in case you'd removed one package too many.

Also, you should be able to access CUPS using your web browser at localhost:631.  You can view the error log on the administration page.

---

### Post by bookcrazy on 2011-11-25
> **Sazhen86 said:**
> Also, you should be able to access CUPS using your web browser at localhost:631.

Thank you for your reply. I added the package you mentioned, restarted my computer, and nothing :( 

As for CUPS, when I go to localhost:631 and click "Add Printer" it prompts me for my password and I have no clue what that is. 

Sorry to be such a downer but I really do thank you for your efforts with this one.

---

### Post by Sazhen86 on 2011-11-25
You can use your own login username and password for CUPS.  Can you check that your user is part of the lpadmin group?

---

### Post by bookcrazy on 2011-11-27
> **Sazhen86 said:**
> You can use your own login username and password for CUPS.  Can you check that your user is part of the lpadmin group?

Thank you! After experimenting I was finally able to get onto Cups and I am part of the lpadmin group. 

Unfortunately, I really don't know what to do next. Any advice?

---

### Post by Sazhen86 on 2011-11-27
If you can print test pages, then it sounds like your printer connection and driver are OK.  Can you take a look in /var/log/cups/error_log and /var/log/lpr.log to see if any errors are reported when you try to print?  

Also, what happens if you try to print from the command line using lpr?

Finally, what is the output from lpstat -t

---

### Post by bookcrazy on 2011-11-27
> **Sazhen86 said:**
> If you can print test pages, then it sounds like your printer connection and driver are OK.  Can you take a look in /var/log/cups/error_log 

```
I [28/Nov/2011:07:12:28 +0800] Saving job cache file "/var/cache/cups/job.cache"...
D [28/Nov/2011:07:12:28 +0800] Discarding unused printer-stopped event...
D [28/Nov/2011:07:12:28 +0800] cupsdMarkDirty(P-----)
D [28/Nov/2011:07:12:28 +0800] cupsdSetBusyState: Dirty files
D [28/Nov/2011:07:12:28 +0800] cupsdDeregisterPrinter(p=0x20e666b0(109Printer), removeit=1)
D [28/Nov/2011:07:12:28 +0800] Discarding unused printer-stopped event...
D [28/Nov/2011:07:12:28 +0800] cupsdMarkDirty(P-----)
D [28/Nov/2011:07:12:28 +0800] cupsdDeregisterPrinter(p=0x20e69088(HP-LaserJet-1010), removeit=1)
I [28/Nov/2011:07:12:28 +0800] Loaded MIME database from "/usr/share/cups/mime" and "/etc/cups": 37 types, 77 filters...
D [28/Nov/2011:07:12:28 +0800] Loading printer 109Printer...
D [28/Nov/2011:07:12:28 +0800] load_ppd: Loading /var/cache/cups/109Printer.ipp...
D [28/Nov/2011:07:12:28 +0800] cupsdRegisterPrinter(p=0x20e64360(109Printer))
D [28/Nov/2011:07:12:28 +0800] Loading printer HP-LaserJet-1010...
D [28/Nov/2011:07:12:28 +0800] load_ppd: Loading /var/cache/cups/HP-LaserJet-1010.ipp...
D [28/Nov/2011:07:12:28 +0800] cupsdRegisterPrinter(p=0x20e939e0(HP-LaserJet-1010))
I [28/Nov/2011:07:12:28 +0800] Loading job cache file "/var/cache/cups/job.cache"...
D [28/Nov/2011:07:12:28 +0800] [Job 1] Loading from cache...
D [28/Nov/2011:07:12:28 +0800] [Job 2] Loading from cache...
D [28/Nov/2011:07:12:28 +0800] [Job 3] Loading from cache...
```

> and /var/log/lpr.log 

lpr.log is empty but lpr.log.1 contained this:

```
 Nov 23 09:50:14 work-laptop udev-configure-printer: add /module/lp
Nov 23 09:50:14 work-laptop udev-configure-printer: Failed to get parent] 
```

> Also, what happens if you try to print from the command line using lpr?

I am really sorry but I cannot figure for the life of me how to print using lpr. 

> Finally, what is the output from lpstat -t

```
scheduler is running
system default destination: HP-LaserJet-1010
device for HP-LaserJet-1010: smb://JCIE/109PRINTSRV/OFFICE109
HP-LaserJet-1010 accepting requests since Mon 28 Nov 2011 10:14:22 AM CST
printer HP-LaserJet-1010 is idle.  enabled since Mon 28 Nov 2011 10:14:22 AM CST
	Processing page 2...
HP-LaserJet-1010-274    work                 0   Mon 28 Nov 2011 10:45:32 AM CST
```

Thanks a million for all your help with this!

---

### Post by Sazhen86 on 2011-11-28
Hi!

The output from lpstat -t says that your printer is using the smb protocol which means that your printer is attached to a windows print server:

> device for HP-LaserJet-1010: smb://JCIE/109PRINTSRV/OFFICE109


Can you describe how your printer is connected?

As printing has worked before, there may be a problem with the smbspool configuration.

No worries about helping you out.  I just hope that we can get it working for you :-)

---

### Post by bookcrazy on 2011-11-28
My computer is connected to a Windows printer using Samba. The printer is on the company's domain but my computer is apart of the network but not apart of the domain because I dual boot Windows anytime I need to log on to the domain. I was able to print with absolutely no problems what so ever until I must have accidentally uninstalled something vital when I purged Kubuntu. 

Good news! After rebooting, updating, uninstalling and reinstalling the printer several times, it now prints. 

Unfortunately, it prints what I want but then it prints an extra page that says ```
Unsupported Personality: PCL
``` 

The good news is that I found this thread [http://ubuntuforums.org/showthread.php?p=85249](http://ubuntuforums.org/showthread.php?p=85249) where the people say they found a solution. The bad news is the website is down for maintenance [http://www.linuxprinting.org/ppd-o-m...et_1012&show=0](http://www.linuxprinting.org/ppd-o-m...et_1012&show=0) :) Oh well, looks like I'll just have more recycle paper for a while.

Seriously Sazhen86, thank you for your help.

---

### Post by bookcrazy on 2011-11-29
I was looking through all the packages that I uninstalled and one of them was "python-packagekit" so I installed that, rebooted and now the printer is no longer printing an extra page that says: "Unsupported Personality: PCL"

Life is good. Thank you so much Sazhen86 for all your help with this problem!

---

### Post by Sazhen86 on 2011-11-29
That's great to hear!  It's always good when a problem is solved.  Not sure I helped too much though!

---

### Post by bookcrazy on 2011-12-08
And a final postscript to this whole annoying saga:

A few days after thinking everything was fine, I lost the ability to print again after doing a standard ```
sudo apt-get update && sudo apt-get upgrade
``` I was so annoyed that I just said "**** it!" and decided to do a fresh install from a live CD so I backed everything up with deja-dup and got braced.

Sure enough, everything now works just as well as it did before I started playing around with Kubuntu and Edubuntu! Word to the wise: always back up your files because sometimes doing a fresh install really is the easiest way to solve your problems.

---

