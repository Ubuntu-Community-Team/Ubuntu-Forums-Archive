---
title: "adding xfce to ubuntu"
date: 2010-01-06
forum: General Help
---

### Post by dnr1128 on 2010-01-06
I'd like to add x to my current window manager, gnome.  what is the best and cleanest way to download and install it?  command line?  If I don't like it, what's the command to remove it without messing up gnome and any of my programs?

---

### Post by Leppie on 2010-01-06
to install XFCE to your ubuntu installation:
```
sudo apt-get install xubuntu-desktop
```

---

### Post by sisco311 on 2010-01-06
[http://psychocats.net/ubuntu/xfce]("http://psychocats.net/ubuntu/xfce")

---

### Post by nothingspecial on 2010-01-06
```
sudo apt-get install xfce4
```

Then choose it at login.

To remove along with dependencies
```

sudo apt-get remove --purge  a2ps desktop-base exo-utils fortune-mod fortunes-min gtk2-engines-xfce
  libexo-0.3-0 librecode0 libthunar-vfs-1-2 libxcb-keysyms1 libxfce4menu-0.1-0
  libxfce4util4 libxfcegui4-4 libxfconf-0-2 orage psutils tango-icon-theme
  thunar thunar-data thunar-volman wdiff xfce4 xfce4-appfinder xfce4-mixer
  xfce4-panel xfce4-session xfce4-settings xfce4-utils xfce4-volumed xfconf
  xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes
```

---

### Post by nothingspecial on 2010-01-06
> **Leppie said:**
> to install XFCE to your ubuntu installation:
```
sudo apt-get install xubuntu-desktop
```

I think he was just talking about xfce, not xubuntu and everything else that goes with it.

---

### Post by Leppie on 2010-01-06
> **nothingspecial said:**
> I think he was just talking about xfce, not xubuntu and everything else that goes with it.
what is "everything else that goes with it"? those are mostly packages already installed with ubuntu (gnome de), if he decides to remove the gnome de he won't be left with a "bare" xfce this way.

---

### Post by nothingspecial on 2010-01-06
> **Leppie said:**
> what is "everything else that goes with it"?

xubuntu desktop = a2ps abiword abiword-common abiword-help abiword-plugin-grammar
  abiword-plugin-mathview abiword-plugins app-install-data-commercial catfish
  exaile exo-utils feh fortune-mod fortunes-min giblib1 gigolo
  gnome-app-install gnumeric gnumeric-common gnumeric-doc gtk2-engines-xfce
  imagemagick libaiksaurus-1.2-0c2a libaiksaurus-1.2-data
  libaiksaurusgtk-1.2-0c2a libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a
  libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgoffice-0-8
  libgoffice-0-8-common libgtkmathview0c2a libimlib2 liblink-grammar4 libotr2
  libots0 libpolkit-dbus2 libpolkit-gnome0 libpolkit-grant2 libpolkit2
  libreadline5 librecode0 libscim8c2a libt1-5 libtagc0 libthunar-vfs-1-2
  libwv-1.2-3 libxcb-keysyms1 libxfce4menu-0.1-0 libxfce4util4 libxfcegui4-4
  libxfconf-0-2 libxmlrpc-core-c3 link-grammar-dictionaries-en mousepad orage
  pidgin pidgin-data pidgin-libnotify pidgin-otr policykit policykit-gnome
  psutils python-cddb python-mutagen ristretto scim scim-bridge-agent
  scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket
  scim-modules-table scim-tables-additional tango-icon-theme
  tango-icon-theme-common tcl thunar thunar-archive-plugin thunar-data
  thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird
  ttf-arphic-uming usb-creator usplash-theme-xubuntu vim-runtime wdiff xchat
  xchat-common xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin
  xfce4-cpugraph-plugin xfce4-dict xfce4-fsguard-plugin xfce4-mailwatch-plugin
  xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin
  xfce4-panel xfce4-places-plugin xfce4-power-manager xfce4-power-manager-data
  xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings
  xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal
  xfce4-utils xfce4-verve-plugin xfce4-volumed xfce4-weather-plugin
  xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4 xfswitch-plugin
  xfwm4 xfwm4-themes xubuntu-artwork xubuntu-artwork-usplash
  xubuntu-default-settings xubuntu-desktop xubuntu-docs xubuntu-gdm-theme
  xubuntu-wallpapers


xfce4 = a2ps desktop-base exo-utils fortune-mod fortunes-min gtk2-engines-xfce
  libexo-0.3-0 librecode0 libthunar-vfs-1-2 libxcb-keysyms1 libxfce4menu-0.1-0
  libxfce4util4 libxfcegui4-4 libxfconf-0-2 orage psutils tango-icon-theme
  thunar thunar-data thunar-volman wdiff xfce4 xfce4-appfinder xfce4-mixer
  xfce4-panel xfce4-session xfce4-settings xfce4-utils xfce4-volumed xfconf
  xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes


Bit of a difference, wouldn`t you say?

 > I'd like to add x to my current window manager, gnome. what is the best and [COLOR="Red"]cleanest way[/COLOR] to download and install it?

Maybe I interpreted the question incorrectly.

---

### Post by Leppie on 2010-01-06
since when is clean a synonym of bare???

also as i wrote you in my previous post, most of the packages present in the xubuntu install are part of the ubuntu install as well (so i don't really understand why you listed all those packages in your last post).

---

### Post by nothingspecial on 2010-01-06
> **Leppie said:**
> (so i don't really understand why you listed all those packages in your last post).

Because those are the dependencies that apt-get wants to install when told to install xubuntu-desktop and xfce4 respectively on my Ubuntu install.

So they obviously are not included in ubuntu - pidgin, abiword, feh ......etc, etc and all their dependencies.

You don`t have to install xubuntu to _try_ xfce.

---

### Post by Leppie on 2010-01-06
no, you don't have to install xubuntu to try xfce.
but in your optics, a clean Ubuntu install would mean an Ubuntu minimal install.
as i pointed out before, to me clean doesn't mean minimal...

furthermore, are you suggesting you have not removed anything from your standard Ubuntu install (that would be a bit hard to believe, ***_if_*** you did a standard Ubuntu install)?

---

### Post by nothingspecial on 2010-01-06
> **Leppie said:**
> no, you don't have to install xubuntu to try xfce.
but in your optics, a clean Ubuntu install would mean an Ubuntu minimal install.
as i pointed out before, to me clean doesn't mean minimal...

furthermore, are you suggesting you have not removed anything from your standard Ubuntu install (that would be a bit hard to believe, ***_if_*** you did a standard Ubuntu install)?

I only installed this morning and haven`t removed anything actually. (Except for ffmpeg and libx264-dev which weren`t installed anyway, and thttpd which I installed with the previous command)

```

  317  sudo apt-get install unetbootin
  333  sudo apt-get update
  335  sudo apt-get update
  340  sudo apt-get install thttpd
  347  sudo apt-get remove thttpd
  355  sudo apt-get install mpd
  356  sudo apt-get install soundconverter
  397  sudo apt-get upgrade
  409  sudo apt-get remove ffmpeg x264 libx264-dev
  410  sudo apt-get install build-essential subversion git-core checkinstall yasm texi2html libfaac-dev libfaad-dev libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev libsdl1.2-dev libx11-dev libxfixes-dev libxvidcore4-dev zlib1g-dev
  417  sudo apt-get install libogg-dev
  431  sudo apt-get install winff
  432  sudo apt-get install gtkpod-aac
  453  sudo apt-get install xfce
  454  sudo apt-get install xfce4
  455  sudo apt-get install xubuntu-desktop
  457  sudo apt-get install mplayer-nogui
  501  history | grep apt-get
  502  history | grep apt-get | less
```

Line 317 was the last apt-get command of my old crunchbang install, obviously getting unetbootin, to install Ubuntu. Line 454 and 455 are me, seeing what is installed along with those 2 packages. So yes, those lists of packages are what you install with a pretty much vanilla Ubuntu desktop install.


The thread title is > adding xfce to ubuntu not installing xubuntu.

---

### Post by SecretCode on 2010-01-06
> **nothingspecial said:**
> xubuntu desktop = ...

xfce4 = ...

Bit of a difference, wouldn`t you say?

 

Maybe I interpreted the question incorrectly.

Similar picture here, on a full Ubuntu install:
```
$ sudo aptitude install xubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  a2ps{a} abiword abiword-common{a} abiword-help{a} abiword-plugin-grammar{a} abiword-plugin-mathview{a} abiword-plugins 
  app-install-data-commercial catfish exo-utils{a} feh{a} fortune-mod{a} fortunes-min{a} gigolo gnome-app-install gnumeric 
  gnumeric-common{a} gnumeric-doc{a} gtk2-engines-xfce libaiksaurus-1.2-0c2a{a} libaiksaurus-1.2-data{a} 
  libaiksaurusgtk-1.2-0c2a{a} libexo-0.3-0{a} libgdome2-0{a} libgdome2-cpp-smart0c2a{a} libgoffice-0-8{a} 
  libgoffice-0-8-common{a} libgtkmathview0c2a{a} liblink-grammar4{a} libotr2{a} libots0{a} libpolkit-dbus2{a} 
  libpolkit-gnome0{a} libpolkit-grant2{a} libpolkit2{a} librecode0{a} libscim8c2a{a} libt1-5{a} libthunar-vfs-1-2{a} 
  libwv-1.2-3{a} libxcb-keysyms1{a} libxfce4menu-0.1-0{a} libxfce4util4{a} libxfcegui4-4{a} libxfconf-0-2{a} 
  libxmlrpc-core-c3{a} link-grammar-dictionaries-en{a} mousepad orage pidgin pidgin-data{a} pidgin-libnotify{a} pidgin-otr 
  policykit{a} policykit-gnome ristretto scim scim-bridge-agent{a} scim-bridge-client-gtk{a} scim-gtk2-immodule{a} 
  scim-modules-socket{a} tango-icon-theme tango-icon-theme-common tcl{a} thunar thunar-archive-plugin thunar-data{a} 
  thunar-media-tags-plugin thunar-thumbnailers thunar-volman{a} thunderbird ttf-arphic-uming usb-creator 
  usplash-theme-xubuntu{a} vim-runtime wdiff{a} xchat xchat-common{a} xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin 
  xfce4-cpugraph-plugin xfce4-dict xfce4-fsguard-plugin xfce4-mailwatch-plugin xfce4-mixer{a} xfce4-mount-plugin 
  xfce4-netload-plugin xfce4-notes-plugin xfce4-panel{a} xfce4-places-plugin xfce4-power-manager{a} xfce4-power-manager-data{a} 
  xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings{a} xfce4-smartbookmark-plugin 
  xfce4-systemload-plugin xfce4-terminal xfce4-utils{a} xfce4-verve-plugin xfce4-volumed{a} xfce4-weather-plugin 
  xfce4-xkb-plugin xfconf{a} xfdesktop4{a} xfdesktop4-data{a} xfprint4 xfswitch-plugin xfwm4{a} xfwm4-themes{a} 
  xubuntu-artwork{a} xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs xubuntu-gdm-theme{a} 
  xubuntu-wallpapers{a} 
The following packages will be REMOVED:
  ubuntu-xsplash-artwork{a} 
0 packages upgraded, 119 newly installed, 1 to remove and 0 not upgraded.
Need to get 96.3MB of archives. After unpacking 346MB will be used.
```

```
$ sudo aptitude install xfce4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  a2ps{a} desktop-base{a} exo-utils{a} fortune-mod{a} fortunes-min{a} gtk2-engines-xfce{a} libexo-0.3-0{a} librecode0{a} 
  libthunar-vfs-1-2{a} libxcb-keysyms1{a} libxfce4menu-0.1-0{a} libxfce4util4{a} libxfcegui4-4{a} libxfconf-0-2{a} orage{a} 
  tango-icon-theme{a} thunar{a} thunar-data{a} thunar-volman{a} wdiff{a} xfce4 xfce4-appfinder{a} xfce4-mixer{a} xfce4-panel{a} 
  xfce4-session{a} xfce4-settings{a} xfce4-utils{a} xfce4-volumed{a} xfconf{a} xfdesktop4{a} xfdesktop4-data{a} xfprint4{a} 
  xfwm4{a} xfwm4-themes{a} 
0 packages upgraded, 34 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.7MB of archives. After unpacking 96.4MB will be used.

```

It definitely seems to me that installing xfce4 is the better first step.

---

### Post by dnr1128 on 2010-01-06
I currently have gnome on my karmic installation.  I want to try the different desktop environment, xfce.  Sorry for any confusion.  

If I don't like it, I want to be able to remove it so that my system returns to the way it was previous to installing it

---

### Post by kellemes on 2010-01-06
> **dnr1128 said:**
> if i don't like it, i want to be able to remove it so that my system returns to the way it was previous to installing it

You can always remove XFCE with ease..
```
sudo apt-get install xfce4
```
now you can choose XFCE from you loginscreen.

You will like it, XFCE is just great!

---

### Post by dnr1128 on 2010-01-06
I installed it, but the graphics aren't working properly.  For instance, when I open OO writer, things look normal except for the menus...instead of "file" all I see is something like ---, the same for the other menus.  Also, I have been running desklets and they're not working properly either.  All I see is lines.  I looked in the graphics settings, and all it had was resolution and refresh rate.  How do I fix it?

I have the same thing happen when i try to open up system monitor.  just blue lines.

---

### Post by nothingspecial on 2010-01-07
I have no idea what could be wrong. I`ve just installed it myself to check and it`s running great. I`ve not used it in ages and I might just keep it around. I kind of prefer openbox for speed, but you never know I might get used to it.

Did you have any graphics/video/display problems in gnome?

---

### Post by oldos2er on 2010-01-07
> **dnr1128 said:**
> If I don't like it, I want to be able to remove it so that my system returns to the way it was previous to installing it


[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

---

### Post by nothingspecial on 2010-01-07
> **oldos2er said:**
> [http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

Yeah, but he`s only installed xfce4 not xubuntu-desktop so instead of all that simply 
```

sudo apt-get remove --purge  a2ps desktop-base exo-utils fortune-mod fortunes-min gtk2-engines-xfce
  libexo-0.3-0 librecode0 libthunar-vfs-1-2 libxcb-keysyms1 libxfce4menu-0.1-0
  libxfce4util4 libxfcegui4-4 libxfconf-0-2 orage psutils tango-icon-theme
  thunar thunar-data thunar-volman wdiff xfce4 xfce4-appfinder xfce4-mixer
  xfce4-panel xfce4-session xfce4-settings xfce4-utils xfce4-volumed xfconf
  xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes
```

Why is everyone expecting/advising/wanting him to install xubuntu? He just wants to try xfce???????

---

