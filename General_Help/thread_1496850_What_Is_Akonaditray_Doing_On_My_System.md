---
title: "What Is Akonaditray Doing On My System?"
date: 2010-05-29
forum: General Help
---

### Post by Jakiejake on 2010-05-29
Hi
Im just wondering What Is akonaditray Doing On My System?
Did it come default with Ubuntu 10.04? How did I get it
Please Help

---

### Post by Dallas.Dude on 2010-05-29
Even i have the same doubt?
It is not there when installed... 
What exactly is it???

---

### Post by wojox on 2010-05-29
[Quick forum search]("http://ubuntuforums.org/showthread.php?t=1305105")

---

### Post by Jakiejake on 2010-05-29
> **wojox said:**
> [Quick forum search]("http://ubuntuforums.org/showthread.php?t=1305105")

Thanks

---

### Post by Jakiejake on 2010-05-29
> **wojox said:**
> [Quick forum search]("http://ubuntuforums.org/showthread.php?t=1305105")

I tried Google first, nothing good :)

---

### Post by wojox on 2010-05-29
Are you running kde or gnome?

---

### Post by Jakiejake on 2010-05-29
How do I remove it
I probably got it from a KDE program which I just removed but Akondaitray Is not in the package manager to unistall

---

### Post by wojox on 2010-05-29
> **Jakiejake said:**
> How do I remove it
I probably got it from a KDE program which I just removed but Akondaitray Is not in the package manager to unistall

When you search **Akonadi ** is anything marked?

---

### Post by Jakiejake on 2010-05-29
> **wojox said:**
> Are you running kde or gnome?

I am using Gnome

---

### Post by Jakiejake on 2010-05-29
> **wojox said:**
> When you search **Akonadi ** is anything marked?
Here is what is marked...
akonadi-server
kdepim-runtime
libakonadiprivate1
mysql-client-core-5.1
mysql-server-core-5.1
python-kde4

---

### Post by wojox on 2010-05-29
> **Jakiejake said:**
> 
akonadi-server
kdepim-runtime
libakonadiprivate1
python-kde4

Try uninstalling those packages but make sure it dosen't take anything else with it.

---

### Post by Jakiejake on 2010-05-29
> **wojox said:**
> Try uninstalling those packages but make sure it dosen't take anything else with it.

That's why im worried
Are you sure I won't need them?

---

### Post by wojox on 2010-05-29
You shouldn't if your running Gnome. Try running this in the terminal and see what it says:

```
sudo apt-get purge akonadi-server kdepim-runtime libakonadiprivate1 python-kde4
```

---

### Post by Jakiejake on 2010-05-29
> **wojox said:**
> You shouldn't if your running Gnome. Try running this in the terminal and see what it says:

```
sudo apt-get purge akonadi-server kdepim-runtime libakonadiprivate1 python-kde4
```

jacob@jacob-desktop:~$ sudo apt-get purge akonadi-server kdepim-runtime libakonadiprivate1 python-kde4
[sudo] password for jacob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libflite1 libfftw3-3 libgme0 freepats libiptcdata0 libwildmidi0 liborc-0.4-0
  libkate1 libcdaudio1 libmimic0 libsoundtouch1c2 libcelt0-0 libdirac-encoder0
  libofa0 libmms0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  akonadi-server* gdebi-kde* install-package* kdebase-workspace-bin*
  kdebase-workspace-data* kdepim-runtime* kdepimlibs5* kpackagekit*
  kubuntu-debug-installer* libakonadiprivate1* plasma-dataengines-workspace*
  plasma-widgets-workspace* python-kde4* software-properties-kde*
  update-manager-kde*
0 upgraded, 0 newly installed, 15 to remove and 0 not upgraded.
After this operation, 82.9MB disk space will be freed.
Do you want to continue [Y/n]?
What should I press

---

### Post by wojox on 2010-05-29
You can uninstall them. Their all KDE apps and libs.

---

### Post by Jakiejake on 2010-05-29
jacob@jacob-desktop:~$ sudo apt-get purge akonadi-server kdepim-runtime libakonadiprivate1 python-kde4
[sudo] password for jacob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libflite1 libfftw3-3 libgme0 freepats libiptcdata0 libwildmidi0 liborc-0.4-0
  libkate1 libcdaudio1 libmimic0 libsoundtouch1c2 libcelt0-0 libdirac-encoder0
  libofa0 libmms0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  akonadi-server* gdebi-kde* install-package* kdebase-workspace-bin*
  kdebase-workspace-data* kdepim-runtime* kdepimlibs5* kpackagekit*
  kubuntu-debug-installer* libakonadiprivate1* plasma-dataengines-workspace*
  plasma-widgets-workspace* python-kde4* software-properties-kde*
  update-manager-kde*
0 upgraded, 0 newly installed, 15 to remove and 0 not upgraded.
After this operation, 82.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 165414 files and directories currently installed.)
Removing kubuntu-debug-installer ...
Removing kpackagekit ...
Removing kdebase-workspace-bin ...
Purging configuration files for kdebase-workspace-bin ...
Removing plasma-widgets-workspace ...
Removing kdepim-runtime ...
Purging configuration files for kdepim-runtime ...
Removing akonadi-server ...
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
Purging configuration files for akonadi-server ...
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
Removing software-properties-kde ...
Removing install-package ...
Removing gdebi-kde ...
Removing kdebase-workspace-data ...
Purging configuration files for kdebase-workspace-data ...
Removing update-manager-kde ...
Removing python-kde4 ...
Removing plasma-dataengines-workspace ...
Removing kdepimlibs5 ...
Purging configuration files for kdepimlibs5 ...
Removing libakonadiprivate1 ...
Purging configuration files for libakonadiprivate1 ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_AU.utf8.cache...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for python-support ...
jacob@jacob-desktop:~$

---

### Post by wojox on 2010-05-29
Now run:

```
sudo apt-get autoremove
```

---

### Post by Jakiejake on 2010-05-29
> **wojox said:**
> Now run:

```
sudo apt-get autoremove
```

jacob@jacob-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  freepats kdebase-workspace-kgreet-plugins kdepimlibs-data kdesudo ksysguardd
  libboost-program-options1.40.0 libcdaudio1 libcelt0-0 libdirac-encoder0
  libfftw3-3 libflite1 libgme0 libiptcdata0 libkate1 libkfontinst4
  libkscreensaver5 libksgrd4 libmimic0 libmms0 libofa0 liborc-0.4-0
  libpackagekit-glib2-12 libpackagekit-qt-12 libplasma-applet-system-monitor4
  libplasma-geolocation-interface4 libplasmaclock4 libplasmagenericshell4
  libprocesscore4 libprocessui4 libqimageblitz4 libqt4-help libqt4-scripttools
  libsolidcontrol4 libsolidcontrolifaces4 libsoundtouch1c2 libtaskmanager4
  libweather-ion4 libwildmidi0 mysql-client-core-5.1 mysql-server-core-5.1
  packagekit packagekit-backend-apt phonon python-packagekit python-qt4
  python-sip
0 upgraded, 0 newly installed, 46 to remove and 0 not upgraded.
After this operation, 91.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 164304 files and directories currently installed.)
Removing freepats ...
Removing kdebase-workspace-kgreet-plugins ...
Removing kdepimlibs-data ...
Removing kdesudo ...
update-alternatives: using /usr/lib/kde4/libexec/kdesu-distrib/kdesu to provide /usr/lib/kde4/libexec/kdesu (kdesu) in auto mode.
Removing ksysguardd ...
Removing libboost-program-options1.40.0 ...
Removing libcdaudio1 ...
Removing libcelt0-0 ...
Removing libdirac-encoder0 ...
Removing libofa0 ...
Removing libfftw3-3 ...
Removing libflite1 ...
Removing libgme0 ...
Removing libiptcdata0 ...
Removing libkate1 ...
Removing libkfontinst4 ...
Removing libkscreensaver5 ...
Removing libksgrd4 ...
Removing libmimic0 ...
Removing libmms0 ...
Removing liborc-0.4-0 ...
Removing packagekit ...
Removing libpackagekit-glib2-12 ...
Removing libpackagekit-qt-12 ...
Removing libplasma-applet-system-monitor4 ...
Removing libplasma-geolocation-interface4 ...
Removing libplasmaclock4 ...
Removing libplasmagenericshell4 ...
Removing libprocessui4 ...
Removing libprocesscore4 ...
Removing libqimageblitz4 ...
Removing python-qt4 ...
Removing libqt4-help ...
Removing libqt4-scripttools ...
Removing libsolidcontrol4 ...
Removing libsolidcontrolifaces4 ...
Removing libsoundtouch1c2 ...
Removing libtaskmanager4 ...
Removing libweather-ion4 ...
Removing libwildmidi0 ...
Removing mysql-client-core-5.1 ...
Removing mysql-server-core-5.1 ...
Removing packagekit-backend-apt ...
Removing phonon ...
Removing python-packagekit ...
Removing python-sip ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
jacob@jacob-desktop:~$

---

### Post by Jakiejake on 2010-05-29
> **Jakiejake said:**
> jacob@jacob-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  freepats kdebase-workspace-kgreet-plugins kdepimlibs-data kdesudo ksysguardd
  libboost-program-options1.40.0 libcdaudio1 libcelt0-0 libdirac-encoder0
  libfftw3-3 libflite1 libgme0 libiptcdata0 libkate1 libkfontinst4
  libkscreensaver5 libksgrd4 libmimic0 libmms0 libofa0 liborc-0.4-0
  libpackagekit-glib2-12 libpackagekit-qt-12 libplasma-applet-system-monitor4
  libplasma-geolocation-interface4 libplasmaclock4 libplasmagenericshell4
  libprocesscore4 libprocessui4 libqimageblitz4 libqt4-help libqt4-scripttools
  libsolidcontrol4 libsolidcontrolifaces4 libsoundtouch1c2 libtaskmanager4
  libweather-ion4 libwildmidi0 mysql-client-core-5.1 mysql-server-core-5.1
  packagekit packagekit-backend-apt phonon python-packagekit python-qt4
  python-sip
0 upgraded, 0 newly installed, 46 to remove and 0 not upgraded.
After this operation, 91.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 164304 files and directories currently installed.)
Removing freepats ...
Removing kdebase-workspace-kgreet-plugins ...
Removing kdepimlibs-data ...
Removing kdesudo ...
update-alternatives: using /usr/lib/kde4/libexec/kdesu-distrib/kdesu to provide /usr/lib/kde4/libexec/kdesu (kdesu) in auto mode.
Removing ksysguardd ...
Removing libboost-program-options1.40.0 ...
Removing libcdaudio1 ...
Removing libcelt0-0 ...
Removing libdirac-encoder0 ...
Removing libofa0 ...
Removing libfftw3-3 ...
Removing libflite1 ...
Removing libgme0 ...
Removing libiptcdata0 ...
Removing libkate1 ...
Removing libkfontinst4 ...
Removing libkscreensaver5 ...
Removing libksgrd4 ...
Removing libmimic0 ...
Removing libmms0 ...
Removing liborc-0.4-0 ...
Removing packagekit ...
Removing libpackagekit-glib2-12 ...
Removing libpackagekit-qt-12 ...
Removing libplasma-applet-system-monitor4 ...
Removing libplasma-geolocation-interface4 ...
Removing libplasmaclock4 ...
Removing libplasmagenericshell4 ...
Removing libprocessui4 ...
Removing libprocesscore4 ...
Removing libqimageblitz4 ...
Removing python-qt4 ...
Removing libqt4-help ...
Removing libqt4-scripttools ...
Removing libsolidcontrol4 ...
Removing libsolidcontrolifaces4 ...
Removing libsoundtouch1c2 ...
Removing libtaskmanager4 ...
Removing libweather-ion4 ...
Removing libwildmidi0 ...
Removing mysql-client-core-5.1 ...
Removing mysql-server-core-5.1 ...
Removing packagekit-backend-apt ...
Removing phonon ...
Removing python-packagekit ...
Removing python-sip ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
jacob@jacob-desktop:~$

Logged Out And Logged Back In
Gone
Thank You

---

### Post by Jakiejake on 2010-05-29
Solved
Thank You :)

---

### Post by wojox on 2010-05-29
Your welcome. :)

---

### Post by JCyberinux on 2010-10-21
I personally thanks for this thread for solving the mystery of the application akonaditray... it's for KDE, but i'm using GNOME... so far.. nothing bad happened after the changes... thanks much! cheers!

---

### Post by Kri5 on 2011-06-12
I'm using Kubuntu 11.04 and I believe that the Akonadi Server and the Akonaditray were installed when I started using Kmail.  However Kmail wasn't to my liking in the end and I went back to Thunderbird.  The problem is that Akonadi keeps popping up requesting the 'pop3 password' even though I no longer use Kmail, in fact Kmail has been un-installed.

Anyone know if Akonadi can be un-installed from Kubuntu?

---

### Post by fabianofcarlos on 2011-09-01
In my case, it was installed along with Kplato a few months ago. I have since given up on plato but had no idea there were left-overs. Thank you guys for all the tips.

---

### Post by Emeraldragon on 2012-04-01
Yes, thanks for the thread. I am using Gnome. I guess the lesson we take from this little exercise, is that we do no use the ubuntu software center for installation of anything. For me, in the future, it will be a resource to search for a piece of software that I need. Once I have that information, I can go to the Synaptic Package Manager to show me what I am downloading prior to installing.
   I was in need of some photo editing software. I downloaded digikam which, for the record, was exceptional for what I needed. It is a great piece of software. If, on the other hand, I knew that it needed akonaditray to run, would never have chosen to install it. The problem is that Akonaditray began to index the sql server in XAMPP and I get a little nervous when another server application begins to index files needed for my website. There was no harm done. Again, thanks for the information included in this thread.

:p

---

### Post by oldos2er on 2012-04-01
Closed, necromancy.

---

