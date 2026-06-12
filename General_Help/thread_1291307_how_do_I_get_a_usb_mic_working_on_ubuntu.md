---
title: "how do I get a usb mic working on ubuntu?"
date: 2009-10-14
forum: General Help
---

### Post by stonba on 2009-10-14
It will not reconize it.Is there somethin I type into the terminal or what?:confused:

---

### Post by eric3_14159 on 2009-11-09
Hard to say. The general pointer first try for this kind of problem is searching Google for the word "Ubuntu" plus the model of the microphone.

That often isn't very useful help, though. So, first, what model microphone is it? What version of Ubuntu are you running?

One thing you need to determine is whether the microphone isn't being detected at all, or if it is but the microphone volume options in Gnome are set to 0.

For the first part, run "lsusb" from a command line without the microphone plugged in, and then again when it is plugged in. If something new shows up, then at least it was recognized.

Alternatively, run "tail -f /var/log/messages" at a command line without the mic plugged in, then plug it in and see what happens. You should get a bunch of lines talking about the device, or an "unknown" message of some kind.

If the microphone does seem to have been noticed by your computer, then try opening the volume control, most likely by clicking on the small meter on your panel and clicking the "Volume Control" button from there. If there is an obvious "Microphone" slider set too low or muted on any of the tabs, then fix that. If not, click Preferences, and look for any tracks labelled Recording and select them. Look through the tabs again for any new sliders which are muted or low.

Try these things and post any interesting results you get.

---

### Post by SirBismuth on 2009-11-09
I got a USB headset's mic. working by following a procedure for Pulseaudio, search this forum for "usb headset" or something like that.

B

---

