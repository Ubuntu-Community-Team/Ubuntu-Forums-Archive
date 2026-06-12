---
title: "multitouch gestures not working in Natty...Please Help!"
date: 2011-05-19
forum: General Help
---

### Post by lumix on 2011-05-19
I've been working on this for weeks, and I can't get my egalax touchscreen to work with gestures in Natty.  I believe I have been booting in Unity, but have tried in the traditional Gnome-top as well.

The screen just works like a one button mouse.  I get out put from the mtdev-test, but nothing from gesture test.  I've tried with and without the egalax-multitouch-driver-common installed.

There is no xorg.conf, but I don't think there should be one.

---

### Post by noah++ on 2011-05-19
Did they work previously? I've never gotten mine to work quite right, just because the multitouch drivers (at least for ThinkPad tablets) aren't mature yet. Basically, if I have to move my fingers about semi-randomly for any gesture to register.

---

### Post by lumix on 2011-05-19
Never yet.  If I run 2 fingers down the screen, the application in focus starts highlighting different blocks of text wildly;  but this is of course only because it's registering each mouse as a single-touch device.

---

### Post by wjtaylor on 2011-05-20
Check to see if the OS is recognizing your multitouch device.

See: [https://wiki.ubuntu.com/Multitouch/Testing/CheckingMTDevice](https://wiki.ubuntu.com/Multitouch/Testing/CheckingMTDevice)

if you don't see a "multitouch" device in the output of lsinput, it isn't being recognized. You might not have the hardware or require a firmware update. Make sure one of your input says "multitouch", not "touch" or other such thing.

WT

---

### Post by lumix on 2011-05-23
It doesn't say "multi"touch, but pinch-zoom works (badly)in Windows 7 on this device.

---

