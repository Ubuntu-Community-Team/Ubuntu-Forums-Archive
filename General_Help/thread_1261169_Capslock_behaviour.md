---
title: "Capslock behaviour"
date: 2009-09-08
forum: General Help
---

### Post by Beazel on 2009-09-08
On my Ubuntu machine I found an option to change the Caps Lock into a Backspace key and I've been using this for the last year or so.

Just made the switch to Xubuntu and I'm looking for a way to do the same as every time I make make a mistake I edND UP DOING THIS...

Many thinks in advance,
BeeAZEL

---

### Post by Beazel on 2009-09-09
Answered this myself with an awful lot of help from this thread:

[http://ubuntuforums.org/showthread.php?t=609528](http://ubuntuforums.org/showthread.php?t=609528)

Make a file like:  /path/to/file/.Xmodmap and put this in it:

!! Make caps lock an additional BackSpace
remove Lock = Caps_Lock
keysym Caps_Lock = BackSpace

Then click Applications > Settings > Session and Startup and switch to the Application Autostart tab.  Click "Add" and fill out the "Command" box with:

xmodmap /path/to/file/.Xmodmap

For some reason unknown the first couple of reboots I was still getting normal Caps Lock behaviour and had to run the above command manually.  No idea why, but it's working automatically now...

---

