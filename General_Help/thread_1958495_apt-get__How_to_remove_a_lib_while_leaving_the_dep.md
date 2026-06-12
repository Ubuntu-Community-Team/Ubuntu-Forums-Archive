---
title: "apt-get / How to remove a lib while leaving the dependencies ?"
date: 2012-04-14
forum: General Help
---

### Post by dargaud on 2012-04-14
As explained [here]("http://linux.tvortex.net/2011/11/spyder-3-on-newer-linux-flavors.html") I would like to remove libmtp, which I don't use (I have my own scripts for music/image copies). If I try it it asks for too much removal:
```
$ sudo apt-get remove libmtp*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libmtp9' for regex 'libmtp*'
Note, selecting 'libmtdev-dev' for regex 'libmtp*'
Note, selecting 'libmtdev1' for regex 'libmtp*'
Note, selecting 'libmtp-common' for regex 'libmtp*'
Note, selecting 'libmtp8' for regex 'libmtp*'
Note, selecting 'libmtp-dbg' for regex 'libmtp*'
Note, selecting 'libmtp-runtime' for regex 'libmtp*'
Note, selecting 'libmtp-dev' for regex 'libmtp*'
Note, selecting 'libmtp-doc' for regex 'libmtp*'
Note, selecting 'libmthca-dev' for regex 'libmtp*'
Note, selecting 'libmthca1' for regex 'libmtp*'
Note, selecting 'libmthca1-dbg' for regex 'libmtp*'
Package libmtdev-dev is not installed, so not removed
Package libmtp-dbg is not installed, so not removed
Package libmtp-dev is not installed, so not removed
Package libmtp-doc is not installed, so not removed
Package libmthca-dev is not installed, so not removed
Package libmthca1 is not installed, so not removed
Package libmthca1-dbg is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libva-x11-1 libglew1.5 projectm-data libxcb-xv0 libtar0 libiso9660-7 libcddb2 libnotify4 libdvbpsi7 libvlc5
  libsdl-image1.2 libupnp3 libmatroska4 libxcb-keysyms1 vlc-data libvlccore4 libvcdinfo0 libebml3 libxcb-randr0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  amarok clementine evince kubuntu-desktop libevince3-3 libgrip0 libmtdev1 libmtp-common libmtp-runtime libmtp9
  libutouch-geis1 libutouch-grail1 vlc vlc-nox vlc-plugin-notify vlc-plugin-pulse xorg xserver-xorg xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-synaptics
0 upgraded, 0 newly installed, 21 to remove and 0 not upgraded.
After this operation, 54.3 MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

---

### Post by dargaud on 2012-04-14
well, removing libmtp-runtime was aparently enough to go the the next stage of problems.

---

### Post by Zorael on 2012-04-14
For what it's worth, if apt wants to remove packages "because they're no longer needed" and you want to keep them, the solution is to mark them as manually installed. Either by trying to install them again or by using **apt-mark**.
```
$ sudo apt-get install libva-x11-1 libglew1.5 projectm-data libxcb-xv0 libtar0 libiso9660-7 libcddb2 libnotify4 libdvbpsi7 libvlc5 libsdl-image1.2 libupnp3 libmatroska4 libxcb-keysyms1 vlc-data libvlccore4 libvcdinfo0 libebml3 libxcb-randr0

*# ...or...*

$ sudo **apt-mark manual** libva-x11-1 libglew1.5 projectm-data libxcb-xv0 libtar0 libiso9660-7 libcddb2 libnotify4 libdvbpsi7 libvlc5 libsdl-image1.2 libupnp3 libmatroska4 libxcb-keysyms1 vlc-data libvlccore4 libvcdinfo0 libebml3 libxcb-randr0
```

**aptitude** also has an **unmarkauto** verb.

---

