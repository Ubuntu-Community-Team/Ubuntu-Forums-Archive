---
title: "Evolution not attatching signature image"
date: 2010-01-14
forum: General Help
---

### Post by msvalente24 on 2010-01-14
I Have searched High and low for a solution both here and on google but cant seem to find one. My problem is my signatures in evolution are set up with images (under the pref > compositions > signatures menu) and they don't seem to be attaching themselves to the outgoing mail, therefore creating an image not found logo on the recipient side. This is quite a recent bug as it used to work fine.

Does anyone have any comments or clues as to why this is happening?

Thanks

---

### Post by donato roque on 2010-01-14
I just want to add my concerns too.  About Evolution.  It isn't just the signature image but all images that you want to put inline.  

It used to be fun to send images using Evolution because of the inline images.  I guess they want to improve it by dropping this particular feature.  

Now I can only send images as attachment.  This wont work with scanned signatures.

---

### Post by howefield on 2010-01-15
Is it all images file types that you can't use ?

One workaround I read about was creating a .pdf of your signature and inserting that into your signature. Not ideal, but may work.

---

### Post by laket on 2010-02-01
I recently updated to 9.10 and ran into the same signature with image problem. Has anybody found a solution yet?

---

### Post by barretr on 2010-02-24
Apparently it's related to the RSS plugin: [https://bugs.launchpad.net/evolution/+bug/51116](https://bugs.launchpad.net/evolution/+bug/51116). Many thanks, antoiner.

---

### Post by laket on 2010-02-25
barretr, do you know how to apply the patch antoiner pointed out?

for now disabling the Evolution RSS plugin resolves the problem for me, since I do not use RSS in Evolution. Though it's not a good solution for others.
It would be nice if someone could point out how to apply patches in evolution, since ubuntu/canonical didn't approve that patch yet...

---

### Post by barretr on 2010-02-25
laket,

One can copy a paste the following into a terminal to apply just the evolution-rss-0.1.4-inline-images.patch:

> sudo apt-get install build-essential evolution-dev intltool libebook1.2-dev libsoup2.4-dev libgtkhtml3.14-dev libgtkhtml-editor-dev libdbus-glib-1-dev xulrunner-1.9.1-dev libwebkit-dev
wget -P /tmp [http://gnome.eu.org/evolution-rss-0.1.4.tar.gz](http://gnome.eu.org/evolution-rss-0.1.4.tar.gz)
wget -P /tmp [http://gnome.eu.org/patches/evolution-rss-0.1.4-inline-images.patch](http://gnome.eu.org/patches/evolution-rss-0.1.4-inline-images.patch)
tar -zxf /tmp/evolution-rss-0.1.4.tar.gz
cd evolution-rss-0.1.4
patch -p1 </tmp/evolution-rss-0.1.4-inline-images.patch
# should respond with: patching file src/parser.c
./configure --prefix=/usr
make 
sudo make install
# for cleanup: cd .. && rm -Rf evolution-rss-0.1.4

Personally, I've applied all the patches for the current version using:

> sudo apt-get install build-essential evolution-dev intltool libebook1.2-dev libsoup2.4-dev libgtkhtml3.14-dev libgtkhtml-editor-dev libdbus-glib-1-dev xulrunner-1.9.1-dev libwebkit-dev
wget -P /tmp [http://gnome.eu.org/evolution-rss-0.1.4.tar.gz](http://gnome.eu.org/evolution-rss-0.1.4.tar.gz) [http://gnome.eu.org/patches/evolution-rss-0.1.4-vers-detect.patch](http://gnome.eu.org/patches/evolution-rss-0.1.4-vers-detect.patch) [http://gnome.eu.org/patches/evolution-rss-0.1.4-empty-source.patch](http://gnome.eu.org/patches/evolution-rss-0.1.4-empty-source.patch) [http://gnome.eu.org/patches/evolution-rss-0.1.4-inline-images.patch](http://gnome.eu.org/patches/evolution-rss-0.1.4-inline-images.patch) [http://gnome.eu.org/patches/evolution-rss-0.1.4-status-icon.patch](http://gnome.eu.org/patches/evolution-rss-0.1.4-status-icon.patch) [http://gnome.eu.org/patches/evolution-rss-0.1.4-recv-feeds3.patch](http://gnome.eu.org/patches/evolution-rss-0.1.4-recv-feeds3.patch) [http://gnome.eu.org/patches/evolution-rss-0.1.4-folder-properties.patch](http://gnome.eu.org/patches/evolution-rss-0.1.4-folder-properties.patch) [http://gnome.eu.org/patches/evolution-rss-0.1.4-folder-rename.patch](http://gnome.eu.org/patches/evolution-rss-0.1.4-folder-rename.patch)
tar -zxf /tmp/evolution-rss-0.1.4.tar.gz
cd evolution-rss-0.1.4
for f in /tmp/evolution-*.patch; do patch -p1 < $f; done
./configure --prefix=/usr
make
sudo make install
# for cleanup: cd .. && rm -Rf evolution-rss-0.1.4

Additionally, compilation & installation instructions (without patching) can be found here:
[http://gnome.eu.org/evo/index.php/Installation](http://gnome.eu.org/evo/index.php/Installation)

---

