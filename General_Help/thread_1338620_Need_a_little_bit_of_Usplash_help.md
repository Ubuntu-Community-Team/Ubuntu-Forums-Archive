---
title: "Need a little bit of Usplash help?"
date: 2009-11-26
forum: General Help
---

### Post by buhmillion on 2009-11-26
I am trying to install a usplash theme that i Downloaded from gnome-look, but the theme came in a folder of seperate images. Resolutions, Throbber-something, etc. How do i compile these into an *.SO file? any help is appreciated.

---

### Post by Anonymousable on 2009-11-26
These are all terminal commands. :)
You'll need to install some building packages...
```
sudo apt-get install cdbs debhelper dpkg-dev fakeroot devscripts autotools-dev
```
Then some more packages needed for the build...
```
sudo apt-get build-dep usplash-theme-ubuntu
```
Then cd to the source folder and actually build it:
```
dpkg-buildpackage -rfakeroot
```

Then to enable it you need to install startup-manager, run it, select appearance, then find the .so file. Select it, close startup-manager and you're done. :)

---

### Post by buhmillion on 2009-11-26
Thanks! Sounds simple enough, i'll try it!

---

