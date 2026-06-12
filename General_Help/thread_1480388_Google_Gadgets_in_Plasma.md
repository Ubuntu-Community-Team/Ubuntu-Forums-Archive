---
title: "Google Gadgets in Plasma"
date: 2010-05-11
forum: General Help
---

### Post by skibum3027 on 2010-05-11
I understand that [COLOR=Blue][this licensing issue]("https://bugs.edge.launchpad.net/ubuntu/+source/google-gadgets/+bug/314778")[/COLOR] is why google gadgets are not included in ubuntu releases.

I found [COLOR=Blue][this guide]("http://www.francescosantini.com/files/ggadgets/google_gadgets_plasmoids_jaunty.txt")[/COLOR] that can install them in Jaunty. I'm trying in Lucid. It seems like it wouldn't need changed much. Here's what I've done:

Install google gadgets library packages:
  ```
sudo apt-get install libggadget-qt-1.0-dev
sudo apt-get install libggadget-1.0-dev
```Install kdebase source and dependencies:
  ```
apt-get source kdebase-workspace
sudo apt-get build-dep kdebase-workspace
```configure the kdebase project:
  ```
cd kdebase-workspace-4.4.3
cmake .
```compile the google gadgets script engine:
  ```
cd plasma/generic/scriptengines/google_gadgets
make
```Copy the binaries:
```
sudo cp ../../../../lib/plasma_package_ggl.so /usr/lib/kde4/plasma_package_ggl.so
sudo cp ../../../../lib/plasma_scriptengine_ggl.so /usr/lib/kde4/plasma_scriptengine_ggl.so
sudo cp plasma-packagestructure-googlegadgets.desktop /usr/share/kde4/services/plasma-packagestructure-googlegadgets.desktop
sudo cp plasma-scriptengine-googlegadgets.desktop /usr/share/kde4/services/plasma-scriptengine-googlegadgets.desktop
sudo cp plasma-applet-ggl.desktop.tmpl /usr/share/kde4/services/plasma-applet-ggl.desktop.tmpl
sudo cp config.txt.tmpl /usr/share/kde4/apps/plasma/plasmoids/ggl/config.txt.tmpl
```Please note that I've tried to modify the locations above to fit kde4.4.3 but I can't actually add the gadgets. The dialog appears for downloading them, but it doesn't seem to do anything when you click add. Can anyone figure out why this doesn't work?

---

### Post by wieman01 on 2010-05-11
You ought to post this under the Tutorials secton. Nice.

---

### Post by skibum3027 on 2010-05-11
Actually it seems to almost work. It crashes regularly still when installing new widgets and frequently screws up the widget's picture, but once the widgets are running they seem to work fine. Still, the crashing is annoying. Is this good enough functionality to consider making this a tutorial?

---

