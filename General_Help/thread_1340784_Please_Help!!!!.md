---
title: "Please Help!!!!"
date: 2009-11-29
forum: General Help
---

### Post by First Sergeant on 2009-11-29
Some time ago I attempted to load Ubuntu from a disc from Ubuntu. It worked at first and then quit. I attempted to download from online again. Now I have a whole series of UBUNTU's on my Toshiba 160 gb drive. Much later I went back and downloaded 9.10 Karmic Koala and it worked like a CHAMP! This still left me with 9.04 and a couple others which do not work as intended. Since my HD was loaded up with over 70% info I wanted to cut 9.10 by eliminating unused programs. The last program I deleted or removed was a Pyton file. I shut down and when I rebooted, my machine came up to a flat black screen asking me to login. I tried and was told it failed. Repated attempts to log in have failed. I hit the F2 and F12 and looked at everything there. Nothing will let me log on. Do you have an answer to these problems? I need to log on and also get rid of the older versions as they are eating up space on the HD. I am a novice Ubuntu user and have used Windows for years. Also, I loaded the UBUNTU into Windows. I know, I know. Dumb. Is there anything I can do short of buying a new computer? VISTA has been good to me, it is just my drive space is at 30%. HELP!

---

### Post by lrcaballero on 2009-11-29
This may NOT be your best option, but I would do it if I was desperate! Try installing Ubuntu again and at the partition section delete the OS's that you don't want. Or if you are dual booting (windows and linux) use partition magic or parttion wizard and delete all unwanted stuff on your HDD. Then you should only have left is Vista on your HDD and now you can install Ubuntu 9.04 or Karmic and either one will take care of the booting menu (GRUB). Let me know if this makes any sence!

Luis

---

### Post by 3rdalbum on 2009-11-29
> **First Sergeant said:**
> Some time ago I attempted to load Ubuntu from a disc from Ubuntu. It worked at first and then quit. I attempted to download from online again. Now I have a whole series of UBUNTU's on my Toshiba 160 gb drive. Much later I went back and downloaded 9.10 Karmic Koala and it worked like a CHAMP! This still left me with 9.04 and a couple others which do not work as intended. Since my HD was loaded up with over 70% info I wanted to cut 9.10 by eliminating unused programs. The last program I deleted or removed was a Pyton file.

It's possible the system could be rebuilt by using a chroot and reinstalling the "ubuntu-desktop" package, but there's no point. You might as well just reinstall Ubuntu 9.10, and this time erase all the earlier partitions you created.

DO NOT do any package installation or removal operations without carefully examining the list of what packages will be changed. The whole system depends on Python. If you mark Python for removal, it gives you the following message:

```
The following packages will be REMOVED:                                                    
  aisleriot alacarte apport apport-gtk apport-hooks-medibuntu apt-xapian-index aptdaemon   
  apturl apturl-common arista at-spi banshee brasero byobu bzr bzrtools capplets-data      
  checkbox checkbox-gtk cheese command-not-found compiz compiz-fusion-plugins-extra        
  compiz-fusion-plugins-main compiz-gnome compizconfig-settings-manager computer-janitor   
  computer-janitor-gtk desktopcouch devede devhelp devhelp-common dput earcandy empathy eog
  evince evolution evolution-couchdb evolution-data-server evolution-documentation-en      
  evolution-exchange evolution-indicator evolution-plugins evolution-webcal f-spot         
  file-roller firefox-3.5-gnome-support firefox-gnome-support firefox-notify gcalctool     
  gconf-editor gconf2 gdebi gdebi-core gdm gdm-guest-session gedit getdeb-repository gimp  
  giver gksu glchess glines gnect gnibbles gnobots2 gnome-about gnome-app-install          
  gnome-applets gnome-applets-data gnome-blackjack gnome-bluetooth gnome-codec-install     
  gnome-control-center gnome-doc-utils gnome-games gnome-keyring gnome-mahjongg gnome-media
  gnome-media-common gnome-menus gnome-orca gnome-panel gnome-panel-data gnome-pilot       
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session                 
  gnome-session-bin gnome-settings-daemon gnome-sudoku gnome-system-monitor                
  gnome-system-tools gnome-terminal gnome-terminal-data gnome-user-guide gnome-utils       
  gnometris gnomine gnotravex gnotski gstreamer0.10-gnomevfs gstreamer0.10-plugins-good    
  gtali gucharmap gweled hpijs hplip hplip-cups hplip-data ia32-libs iagno ibus ibus-m17n  
  ibus-table indicator-applet indicator-applet-session indicator-messages indicator-session
  inkscape iotop jockey-common jockey-gtk kde-minimal kdebase-workspace                    
  kdebase-workspace-bin kdebase-workspace-data kdeutils kscreensaver kscreensaver-xsavers  
  language-selector language-selector-common launchpad-integration libbonoboui2-0          
  libdevhelp-1-0 libempathy-gtk-common libempathy-gtk28 libempathy30 libgail-gnome-module  
  libgksu2-0 libglade2-dev libgnome-media0 libgnome-pilot2 libgnome-vfs2.0-cil libgnome2-0 
  libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomekbd-common   
  libgnomekbd4 libgnomekbdui4 libgnomepanel2.24-cil libgnomeui-0 libgnomevfs2-0            
  libgnomevfs2-common libgnomevfs2-extra libgstfarsight0.10-0 libgweather-common           
  libgweather1 liblpint-bonobo0 libmetacity0 libpanel-applet2-0 libpurple-bin libpurple0   
  libtelepathy-farsight0 libxine1-all-plugins libxine1-gnome lightyears lsb-release        
  metacity metacity-common mousetweaks nautilus nautilus-data nautilus-gksu                
  nautilus-open-terminal nautilus-sendto nautilus-share network-manager                    
  network-manager-gnome nvidia-common onboard openoffice.org-emailmerge                    
  openoffice.org-gnome playonlinux printer-applet python python-apport python-apt          
  python-aptdaemon python-aptdaemon-gtk python-avahi python-axiom python-beautifulsoup     
  python-brasero python-brlapi python-cairo python-celementtree python-central             
  python-chardet python-coherence python-compizconfig python-configglue python-configobj   
  python-couchdb python-crypto python-cups python-cupshelpers python-dbus python-debian    
  python-desktopcouch python-desktopcouch-records python-dev python-distutils-extra        
  python-elementtree python-epsilon python-feedparser python-fstab python-gconf python-gdbm
  python-glade2 python-gmenu python-gnome2 python-gnomeapplet python-gnomecanvas           
  python-gnomekeyring python-gnupginterface python-gobject python-gobject-dev              
  python-gst0.10 python-gtk2 python-gtk2-dev python-gtk2-doc python-gtkhtml2               
  python-gtksourceview2 python-httplib2 python-ibus python-imaging python-kde4
  python-launchpad-integration python-launchpadlib python-lazr-restfulclient
  python-lazr-uri python-libxml2 python-louie python-louis python-lxml python-nevow
  python-newt python-nose python-notify python-numpy python-oauth python-ogg python-openssl
  python-pam python-papyon python-paramiko python-pkg-resources python-problem-report
  python-protobuf python-pyatspi python-pycurl python-pygame python-pygoocanvas
  python-pyinotify python-pyorbit python-pysqlite2 python-pythoncard python-qt4
  python-qt4-dbus python-rdflib python-renderpm python-reportlab python-reportlab-accel
  python-rsvg python-serial python-sexy python-simplejson python-sip4 python-smbc
  python-software-properties python-speechd python-support python-tagpy python-telepathy
  python-twisted-bin python-twisted-conch python-twisted-core python-twisted-names
  python-twisted-web python-ubuntuone-client python-ubuntuone-storageprotocol
  python-uniconvertor python-uno python-utidylib python-virtkey python-vte python-wadllib
  python-webkit python-wnck python-wxgtk2.6 python-wxgtk2.8 python-wxversion python-xapian
  python-xdg python-xkit python-zope.interface pythoncard-tools quickly
  quickly-ubuntu-template rhythmbox same-gnome screen-resolution-extra seahorse skype
  software-center software-properties-gtk soundconverter system-config-printer-common
  system-config-printer-gnome system-config-printer-udev telepathy-butterfly telepathy-haze
  tomboy totem totem-common totem-mozilla totem-plugins totem-plugins-extra transmageddon
  ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-minimal ubuntu-system-service
  ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome ufw unattended-upgrades
  update-manager update-manager-core update-notifier update-notifier-common
  usb-creator-common usb-creator-gtk vinagre vino virtualbox-ose virtualbox-ose-qt
  whichwayisup wine1.2 xulrunner-1.9.1-gnome-support yelp

After this operation, 1,485MB disk space will be freed.
Do you want to continue [Y/n]?
```

It's warning you that this will involve removing half the system. PLEASE read the warnings carefully before removing packages.

---

### Post by earthpigg on 2009-12-12
best bet is a fresh install.

but, ***before you do that***, lets clean up all those other ubuntu installs you have on there... so you aren't so desperate for space in the future that you uninstall the plumbing.

1. back up any important data you have.
2. boot an ubuntu live cd
3. system -> admin -> partition editor.
4. keep the windows one and the 'swap' one, delete the rest.
5. create a new partition using up all the free space you now have. ext4.
6. apply
7. hit that 'install' icon on the desktop, and have it use the partition you just created.




in the future, if you want to uninstall something that came installed by default.... google around a bit or ask us here if it will be safe. it isn't always obvious. who would have known [something named after those old british Monty Python movies]("http://en.wikipedia.org/wiki/Python_(programming_language)") could be system critical?

no one, unless they did a bit of research first... if your handle is accurately indicating your occupation, i am sure you have heard the saying before: proper planning prevents piss poor performance :D

---

