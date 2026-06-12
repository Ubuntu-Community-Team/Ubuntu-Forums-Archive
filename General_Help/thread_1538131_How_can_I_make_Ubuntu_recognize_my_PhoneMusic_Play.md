---
title: "How can I make Ubuntu recognize my Phone/Music Player/SD Card Reader?"
date: 2010-07-24
forum: General Help
---

### Post by Tamber on 2010-07-24
I recently switched to linux from Windows and chose Ubuntu. 

Whenever I plug in either my phone (my main storage transfer device) or music player, they get power, but Ubuntu doesn't seem to think it should do anything with them. No errors, no pop-up windows, nothing. Without any options I don't know how to start on my own, I don't even know what to try.

---

### Post by geoffjay on 2010-07-24
How are you plugging them in? USB? If so try running the command lsusb and see if you're device is in the list. If you've got an ipod (ugh) you might need to install libgpod4.

---

### Post by drewsus on 2010-07-24
First of all, does anything show up in Places -> Computer?
Does anything show up on your desktop? (ie, when I plug in my iPod, or external USB HDD they show up as icons on my desktop). 

Furthermore, try this:
Right-click on the top panel and select "Add to panel..."
Find and select "Disk Mounter" and select "Add"
Does it show any drives (namely the ones you have attached to USB) there?

These are some basic GUI troubleshooting methods that we can try first.

If these fail we can delve further into the arcane depths of the terminal ;)

---

