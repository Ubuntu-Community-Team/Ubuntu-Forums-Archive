---
title: "strange package dependencies...."
date: 2011-07-29
forum: General Help
---

### Post by spiritech on 2011-07-29
hi,

i am trying to un-install some programs however when i mark them for removal it also says that it is going to remove the gnome-desktop-environment plus other much needed packages. i believe this is because they are part of the gnome desktop environment, however i am pretty sure that the gnome desktop can run without these programs. the program i am trying to remove is the gnome-screensaver. i do not think this used to be a problem in earlier releases. is there a round this.. any help..appreciated.

spiritech

---

### Post by mikewhatever on 2011-07-30
Can you post the output of **sudo apt-get -s remove gnome-screensaver**.
The command is a simulation, so it won't remove anything.

---

### Post by spiritech on 2011-07-30
ok i run the simulation and here is the output...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu-xdg gtk2-engines-smooth ekiga libgsf-1-common python-gnomedesktop
  libopal3.6.8 gnome-backgrounds libaiksaurus-1.2-data libgnome2-vfs-perl gtali
  glchess hamster-applet libsrtp0 libdiscid0 gnome-games
  link-grammar-dictionaries-en cheese gdebi libbluray0 libots0 libsvga1 gnobots2
  python-reportlab libgnomepanel2.24-cil rhythmbox libtagc0 libcheese-gtk18
  libgnomevfs2-extra gnome-themes-extras libcdt4 abiword-common lightsoff
  libboost-date-time1.42.0 libmagick++3 python-uniconvertor libgdict-1.0-6
  gdebi-core python-lxml gvfs-bin libgoffice-0.8-8-common libdmapsharing2 seed
  gnibbles python-renderpm dasher gnome-games-extra-data libgoffice-0.8-8
  libbabl-0.0-0 libgegl-0.0-0 liblink-grammar4 libclutter-gtk-0.10-0 ufraw-batch
  gnash-common swell-foop epiphany-extensions gnotski libwv-1.2-3 deskbar-applet
  libesd0 python-gtkglext1 dasher-data gir1.2-clutter-gtk-0.10 gok libgdome2-0
  libpathplan4 libaiksaurusgtk-1.2-0c2a libgsf-1-114 seahorse-plugins cheese-common
  libgnome2-canvas-perl libboost-thread1.42.0 sound-juicer libwmf-bin
  libgtkmathview0c2a liblzo2-2 iagno desktop-base glines esound-common netpbm
  libgvc5 libasyncns0 exiftran gnome-dictionary gimp gedit-plugins libgimp2.0
  libgnome-speech7 liferea libpt2.6.7 gnome-themes-more gnotravex gnect libvdpau1
  quadrapassel libgnome2-perl libnetpbm10 python-gnomeapplet libmusicbrainz3-6
  imagemagick liferea-data libgc1c2 libaiksaurus-1.2-0c2a libmagickcore3-extra
  libgraph4 libabiword-2.8 streamripper gir1.2-gnomegamessupport-1.0
  libloudmouth1-0 gimp-data perlmagick gnome-themes openoffice.org-gnome
  rhythmbox-plugin-cdrecorder inkscape rhythmbox-plugins freeglut3
  gnome-netstatus-applet python-reportlab-accel libgdome2-cpp-smart0c2a
  python-opengl libaudiofile0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  gnome gnome-accessibility gnome-core gnome-desktop-environment gnome-screensaver
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Remv gnome [1:2.30+7ubuntu3]
Remv gnome-accessibility [1:2.30+7ubuntu3]
Remv gnome-desktop-environment [1:2.30+7ubuntu3]
Remv gnome-core [1:2.30+7ubuntu3]
Remv gnome-screensaver [2.30.2-0ubuntu2]

---

### Post by mikewhatever on 2011-07-30
Well,
> The following packages will be REMOVED
gnome gnome-accessibility gnome-core gnome-desktop-environment gnome-screensaver

Nothing major, pretty safe to go forward. I don't see any 'much needed' packages being removed. Do you?

PS: You don't seem to be running an Ubuntu installation. Is it Debian or something else?

---

### Post by spiritech on 2011-07-30
hi

it would seem to me that removing gnome-desktop-environment would leave me without a desktop environment?

and yes i am running ubuntu 11.04. original install was 9.10 from disc and from there run the updates and upgrades all the way upto 11.04... i had to do this because my system crashed and i ended up with no OS at-all. however i have noticed that on the boot console it does have a debian splash logo...

---

### Post by mikewhatever on 2011-07-30
Nope.:p In fact, the gnome-desktop-environment package is not included in the default Ubuntu installation, as well as lots of other packages listed above. You must have installed it and the rest at some point.

---

### Post by spiritech on 2011-07-30
> **mikewhatever said:**
> Nope.:p In fact, the gnome-desktop-environment package is not included in the default Ubuntu installation, as well as lots of other packages listed above. You must have installed it and the rest at some point.

ok then problem is solved... just one thing though if the gnome-desktop-environment is not default in ubuntu, what desktop environment is it using?
and yes i believe it was installed when i installed gnome desktop environment, with extra components from the ubuntu software centre...

---

### Post by srisharan on 2011-07-30
It is just a kind of dummy package dont worry nothing will happen

---

### Post by mikewhatever on 2011-07-30
Ubuntu doesn't have the default Gnome, some packages are removed, others added and all is pulled together by the ubuntu-desktop metapackage. So the environment is still Gnome, just modified.

---

### Post by NightwishFan on 2011-07-30
You can safely remove meta-packages. Also if you notice Debian logos or etc in Ubuntu it happens at times as Ubuntu is based on Debian.

---

### Post by spiritech on 2011-07-30
ok, thank you for your help...

---

### Post by spiritech on 2011-07-30
> **mikewhatever said:**
> Ubuntu doesn't have the default Gnome, some packages are removed, others added and all is pulled together by the ubuntu-desktop metapackage. So the environment is still Gnome, just modified.

ok.. i just checked the synaptic and ubuntu-desktop is not installed. could this be a problem? i reckon it was most probably removed when i removed unity... and so this brings me back to my original question, with new information to light... if i dont have ubuntu-desktop and untity installed will be ok to remove these packages - gnome-desktop-environment gnome-core.

---

### Post by spiritech on 2011-07-30
ok

i went ahead and removed gnome-screensaver package and everything is fine.

thanks for your help. :)

---

### Post by mikewhatever on 2011-07-30
Since you seem to be on a removing spree, you could also remove all the 'automatically installed and are no longer required' packages from post #3. Just run the following:
```
sudo apt-get autoremove
```

---

### Post by spiritech on 2011-07-30
after removing gnome-screensaver and the other packages gnome-desktop-environment and gnome-core. the desktop was fine until i restarted, then i had to manually reload window manager to get my window decorations back. 
all in all it still seems i bit strange that removing gnome-screensaver should remove those other packages.

---

### Post by NightwishFan on 2011-07-30
If only meta-packages are removed you should be fine. For example a metapackage is an empty package that depends on a group of other software. Say (for example) ubuntu-desktop depends on brasero, so if you remove brasero it will want to remove ubuntu-desktop as well, but none of the other stuff ubuntu-desktop installed.

---

### Post by mikewhatever on 2011-07-30
Yeah, it's even stranger that you've had so many non-default packages installed. As for the Gnome desktop environment, it's a bundle of packages that most users find useful. If you don't like that particular bundle, use another, or start with Ubuntu minimal and build on top of that.

---

### Post by spiritech on 2011-08-07
hmmm!

it seems to me that i was associating the ubuntu-desktop-environment with window managers, wallpaper managers and other programs that the all the other programs sit on top of or in.

thanks for your help.

---

