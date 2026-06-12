---
title: "Can I change the user name?"
date: 2009-11-06
forum: General Help
---

### Post by fifoKamb3 on 2009-11-06
Hello,
My current username is administrator and I'd like to use admin.
Is there any way to make this working (without thinking of making another user <admin>) ?

I get this current username by this code:
```
whoami
```
I try to login as **root** using:
```
su root
```
It says:
> su: Authentication failure
Sorry.

During the installation I did not set any other password except the one I am using right now for the user: administrator.

But strange!
When I put this command:
```
sudo su
```
It doesn't ask for the password, I just get the following as result:
> root@serverubuntu:/home/administrator#

Thank you a lot for helping me :)

---

### Post by Shpongle on 2009-11-06
the easiest way to do it would be install ubuntu tweak , that should let you do it , otherwise you gotta edit two files and save them!!, if you only do one of the files then sudo wont work anymore! i cant think of the files off hand but tweak should sort you out, 

peace

---

### Post by louieb on 2009-11-06
**admin** is already taken by a group with the same name - can't use it.

```
When I put this command: sudo su
```

Password is saved for a period of time after the last use of the sudo command.

BTW: **sudo su**  not the safest way to go.

Safer to use 
```
sudo -i
```
more here [RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo") 
and all you need to know here [forum policy on log-in-as-root tutorials - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=716201")

---

### Post by fifoKamb3 on 2009-11-06
tweak?
what is that?
I am using 5.10, 7.10 and 9.10

peace 2 u 2

---

### Post by Shpongle on 2009-11-06
wait that wont work sorry, il get the answer for you now

---

### Post by Shpongle on 2009-11-06
ok this should do it! [http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/](http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/)

tweak is a handy lil prog that provides a gui to configue certain stuff , you can live without it but its handy to have , makes some stuff easy

[http://ubuntu-tweak.com/about](http://ubuntu-tweak.com/about)

---

### Post by hal10000 on 2009-11-06
open a teminal window and do
```
sudo apt-get install ubuntu-tweak
```

---

### Post by fifoKamb3 on 2009-11-06
E: couldn't find package ubuntu-tweak

---

### Post by hal10000 on 2009-11-07
> E: couldn't find package ubuntu-tweak

Edit the file /etc/apt/sources.list (as root) and add the following line at the end of the file:
```

deb http://ppa.launchpad.net/tualatrix/ubuntu **jaunty** main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu **jaunty** main

```
The lines above are valid for jaunty (9.04), if you are using karmic (9.10), you have to replace the jaunty entry with karmic.

Then, on a command-line do:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FE85409EEAB40ECCB65740816AF0E1940624A220

```
then
```
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

---

### Post by fifoKamb3 on 2009-11-07
Thank you hal1000
I'll try that, was that necessarily if I had that tweak application -or whatever it is- on a disk ? **apt-get** looks first in the cd, and then internet, right?

---

### Post by hal10000 on 2009-11-07
ubuntu-tweak is a collection of configuration- and setup utlities,especially for a gnome desktop system. Amongst other tasks you can configure your desktop settings, install software, configure your package-repositories,your boot manager, startup-scripts etc.

You can also do all these tasks with other tools (command line and/or GUI).
e.g. to install software and handle my repositories i usually use synaptic, which i think is the best package manager.

> apt-get looks first in the cd, and then internet, right?
The behaviour of apt-get and other package management tools (synaptic, ubuntu-tweak etc.) depends on the way your apt-system (this is the backend of the most  package management tools) is configured.
The cdrom is usually only activated as a repository during the ubuntu installation. After the first reboot the cdrom gets deactivated and if you install a package, apt looks usually for the latest version of that software, you don' have to care about the place where the software you want to install is stored.
This is just the default behaviour, but the apt system is highly configurable and you can adapt to fit your needs.

---

### Post by fifoKamb3 on 2009-11-07
Media change: please insert the disc labeled
 'Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

I will try that later on 9.10

But on 7.10, I can't install that tweak using:
```
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) gutsy main

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FE85409EEAB40ECCB65740816AF0E1940624A220

sudo apt-get update
sudo apt-get install ubuntu-tweak


```

Thank u anyway ..

---

### Post by fifoKamb3 on 2009-11-07
That's also what's happening while I try to install gedit.

> root@server1:/# sudo apt-get install gedit
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  dbus defoma docbook-xml esound-common fontconfig fontconfig-config gamin
  gconf2 gconf2-common gedit-common gnome-keyring gnome-mime-data iso-codes
  launchpad-integration libart-2.0-2 libaspell15 libatk1.0-0 libaudiofile0
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-glib1
  libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcairo2
  libdatrie0 libdbus-glib-1-2 libenchant1c2a libesd-alsa0 libfontconfig1
  libfreetype6 libgail-common libgail18 libgamin0 libgconf2-4 libglade2-0
  libglib2.0-0 libgnome-keyring0 libgnome2-0 libgnome2-common
  libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1
  libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0
  libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0
  libgnomevfs2-common libgtk2.0-0 libgtk2.0-common libgtksourceview2.0-0
  libgtksourceview2.0-common libhal-storage1 libhal1 libhunspell-1.1-0 libice6
  libidl0 libjpeg62 liblaunchpad-integration0 liborbit2 libpango1.0-0
  libpango1.0-common libpng12-0 libscrollkeeper0 libsm6 libthai-data libthai0
  libtiff4 libx11-6 libx11-data libxau6 libxcomposite1 libxcursor1 libxdamage1
  libxdmcp6 libxext6 libxfixes3 libxft2 libxi6 libxinerama1 libxml2 libxrandr2
  libxrender1 libxslt1.1 mcpp python-cairo python-glade2 python-gobject
  python-gtk2 python-numeric python-pygtksourceview scrollkeeper sgml-base
  sgml-data shared-mime-info ttf-dejavu ttf-dejavu-core ttf-dejavu-extra
  x11-common xml-core
Suggested packages:
  defoma-doc psfontmgr x-ttcidfont-conf dfontmgr docbook docbook-doc
  docbook-dsssl docbook-xsl aspell esound libfreetype6-dev desktop-base
  ttf-kochi-gothic ttf-kochi-mincho ttf-thryomanes ttf-baekmuk
  ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp
  ttf-arphic-bkai00mp mcpp-doc python-glade2-dbg python-gtk2-dbg
  python-numeric-tutorial python-numeric-ext python-numeric-dbg sgml-base-doc
  perlsgml doc-html-w3 opensp libxml2-utils debhelper
Recommended packages:
  libft-perl libgnomevfs2-bin zenity python-gnome2 aspell-en aspell-dictionary
  aspell6a-dictionary libatk1.0-data esound-clients libglib2.0-data cupsys
  gnome-icon-theme libgnomevfs2-extra gnome-mount hicolor-icon-theme
  libgtk2.0-bin
The following NEW packages will be installed:
  dbus defoma docbook-xml esound-common fontconfig fontconfig-config gamin
  gconf2 gconf2-common gedit gedit-common gnome-keyring gnome-mime-data
  iso-codes launchpad-integration libart-2.0-2 libaspell15 libatk1.0-0
  libaudiofile0 libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-glib1 libbonobo2-0 libbonobo2-common libbonoboui2-0
  libbonoboui2-common libcairo2 libdatrie0 libdbus-glib-1-2 libenchant1c2a
  libesd-alsa0 libfontconfig1 libfreetype6 libgail-common libgail18 libgamin0
  libgconf2-4 libglade2-0 libglib2.0-0 libgnome-keyring0 libgnome2-0
  libgnome2-common libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1
  libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0
  libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0
  libgnomevfs2-common libgtk2.0-0 libgtk2.0-common libgtksourceview2.0-0
  libgtksourceview2.0-common libhal-storage1 libhal1 libhunspell-1.1-0 libice6
  libidl0 libjpeg62 liblaunchpad-integration0 liborbit2 libpango1.0-0
  libpango1.0-common libpng12-0 libscrollkeeper0 libsm6 libthai-data libthai0
  libtiff4 libx11-6 libx11-data libxau6 libxcomposite1 libxcursor1 libxdamage1
  libxdmcp6 libxext6 libxfixes3 libxft2 libxi6 libxinerama1 libxml2 libxrandr2
  libxrender1 libxslt1.1 mcpp python-cairo python-glade2 python-gobject
  python-gtk2 python-numeric python-pygtksourceview scrollkeeper sgml-base
  sgml-data shared-mime-info ttf-dejavu ttf-dejavu-core ttf-dejavu-extra
  x11-common xml-core
0 upgraded, 106 newly installed, 0 to remove and 44 not upgraded.
Need to get 17.1MB/25.9MB of archives.
After unpacking 139MB of additional disk space will be used.
Do you want to continue [Y/n]?y
WARNING: The following packages cannot be authenticated!
  libfreetype6 dbus sgml-base xml-core sgml-data docbook-xml esound-common
  libgamin0 gamin libidl0 liborbit2 libxml2 gconf2-common libgconf2-4 gconf2
  libatk1.0-0 libbonobo2-common libbonobo2-0 libpng12-0 libcairo2
  libgtk2.0-common libpango1.0-common libpango1.0-0 libtiff4 libxcomposite1
  libgtk2.0-0 libglade2-0 libaudiofile0 libesd-alsa0 libavahi-common-data
  libavahi-common3 libavahi-client3 libavahi-glib1 libhal-storage1
  gnome-mime-data shared-mime-info libgnomevfs2-common libgnomevfs2-0
  libgnome2-common libgnome2-0 libgail18 libgail-common libgnomecanvas2-common
  libgnomecanvas2-0 libbonoboui2-common libbonoboui2-0 libhunspell-1.1-0
  libenchant1c2a libgnomecups1.0-1 libgnomeprint2.2-data libgnomeprint2.2-0
  libgnomeprintui2.2-common libgnomeprintui2.2-0 gnome-keyring
  libgnome-keyring0 libgnomeui-common libgnomeui-0 libgtksourceview2.0-common
  libgtksourceview2.0-0 launchpad-integration liblaunchpad-integration0
  libxslt1.1 libscrollkeeper0 scrollkeeper gedit-common python-pygtksourceview
  python-numeric python-cairo python-gobject python-gtk2 python-glade2
  iso-codes gedit
Install these packages without verification [y/N]? y
Media change: please insert the disc labeled
 'Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter



---

### Post by hal10000 on 2009-11-07
gedit is a gnome editor, but it seems as if you are working on a command line system, is that right? 

You can do everything with such a system, but you should have mentioned it. instead of gedit you can use nano.

---

