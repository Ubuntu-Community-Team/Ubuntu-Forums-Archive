---
title: "How I can Fix it?"
date: 2010-01-14
forum: General Help
---

### Post by peyek on 2010-01-14
I try update to KDE 4.3.2 after successfully running KDE 4.2.2, and I have an error with this message on my panel.

> This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'

and I follow the instruction, but I have the new error message as below :

> sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-plasma python-dev libeet1 kdebase-bin libqzion0 python2.6-dev
  libqedje0 qt4-qtconfig
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kdebase-workspace-bin
Suggested packages:
  plasma-scriptengines
The following packages will be upgraded:
  kdebase-workspace-bin
1 upgraded, 0 newly installed, 0 to remove and 62 not upgraded.
Need to get 0B/3273kB of archives.
After this operation, 2970kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 202828 files and directories currently installed.)
Preparing to replace kdebase-workspace-bin 4:4.2.2-0ubuntu2 (using .../kdebase-workspace-bin_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_i386.deb) ...
Unpacking replacement kdebase-workspace-bin ...
dpkg: error processing /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kconf_update_bin/plasma-add-shortcut-to-menu', which is also in package kde-window-manager
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Please help...

---

### Post by Mr Nemo on 2010-01-14
Try replacing apt-get with aptitude and see if that corrects the problem.

---

### Post by peyek on 2010-01-14
> **Mr Nemo said:**
> Try replacing apt-get with aptitude and see if that corrects the problem.

Thanks Mr Nemo, and the result when i replacing with aptitude was :

> sudo aptitude install 
[sudo] password for tony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  libkdcraw7{a} libkopete4{a} libqtscriptbindings1{a} libtag-extras0{a} 
  plasma-widget-folderview{a} plasma-widget-networkmanagement{a} 
  printer-applet{a} 
The following packages will be REMOVED:
  libeet1{u} libqedje0{u} libqzion0{u} libzip1{u} python-dev{u} 
  python-plasma{u} python-qt4-common{a} python2.6-dev{u} qt4-qtconfig{u} 
The following packages will be upgraded:
  amarok amarok-common ark cervisia cvsservice dolphin dragonplayer 
  gwenview kamera kate kde-icons-oxygen kde-printer-applet 
  kde-window-manager kde-zeroconf kdebase-plasma kdebase-workspace-bin 
  kdegraphics-strigi-plugins kdemultimedia-kio-plugins kdepasswd 
  kdepim-strigi-plugins kdm kfind khelpcenter4 klipper kmag kmix kmousetool 
  kompare konqueror konqueror-nsplugins konsole kopete krdc krfb ksnapshot 
  ksysguard ksysguardd ksystemlog kuser kwalletmanager libkadm55 libkcddb4 
  libkdecorations4 libkipi6 libkonq5 libkonq5-templates libkrb5-dev 
  libkrb53 libkwineffects1 libokularcore1 libssl-dev libssl0.9.8 
  network-manager-gnome okular okular-extra-backends openssl php5-common 
  php5-dev plasma-widget-network-manager python-kde4 python-qt4 
  python-qt4-dbus python-sip4 system-config-printer-kde systemsettings 
65 packages upgraded, 7 newly installed, 9 to remove and 4 not upgraded.
Need to get 0B/82.9MB of archives. After unpacking 4022kB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 202828 files and directories currently installed.)
Preparing to replace kdebase-workspace-bin 4:4.2.2-0ubuntu2 (using .../kdebase-workspace-bin_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_i386.deb) ...
Unpacking replacement kdebase-workspace-bin ...
dpkg: error processing /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kconf_update_bin/plasma-add-shortcut-to-menu', which is also in package kde-window-manager
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

tony@tony-laptop:~$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  libkdcraw7{a} libkopete4{a} libqtscriptbindings1{a} libtag-extras0{a} 
  plasma-widget-folderview{a} plasma-widget-networkmanagement{a} 
  printer-applet{a} 
The following packages will be REMOVED:
  libeet1{u} libqedje0{u} libqzion0{u} libzip1{u} python-dev{u} 
  python-plasma{u} python-qt4-common{a} python2.6-dev{u} qt4-qtconfig{u} 
The following packages will be upgraded:
  amarok amarok-common ark cervisia cvsservice dolphin dragonplayer 
  gwenview kamera kate kde-icons-oxygen kde-printer-applet 
  kde-window-manager kde-zeroconf kdebase-plasma kdebase-workspace-bin 
  kdegraphics-strigi-plugins kdemultimedia-kio-plugins kdepasswd 
  kdepim-strigi-plugins kdm kfind khelpcenter4 klipper kmag kmix kmousetool 
  kompare konqueror konqueror-nsplugins konsole kopete krdc krfb ksnapshot 
  ksysguard ksysguardd ksystemlog kuser kwalletmanager libkadm55 libkcddb4 
  libkdecorations4 libkipi6 libkonq5 libkonq5-templates libkrb5-dev 
  libkrb53 libkwineffects1 libokularcore1 libssl-dev libssl0.9.8 
  network-manager-gnome okular okular-extra-backends openssl php5-common 
  php5-dev plasma-widget-network-manager python-kde4 python-qt4 
  python-qt4-dbus python-sip4 system-config-printer-kde systemsettings 
65 packages upgraded, 7 newly installed, 9 to remove and 4 not upgraded.
Need to get 0B/82.9MB of archives. After unpacking 4022kB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 202828 files and directories currently installed.)
Preparing to replace kdebase-workspace-bin 4:4.2.2-0ubuntu2 (using .../kdebase-workspace-bin_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_i386.deb) ...
Unpacking replacement kdebase-workspace-bin ...
dpkg: error processing /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kconf_update_bin/plasma-add-shortcut-to-menu', which is also in package kde-window-manager
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done


---

### Post by peyek on 2010-01-14
The bad news is I can't install another applications! :guitar:

---

