---
title: "Gnome-OSD: Can Change Green Text But Yellow Remains. Solution?"
date: 2009-12-16
forum: General Help
---

### Post by OzzyFrank on 2009-12-16
If you use **[COLOR="DarkRed"]Gnome-OSD[/COLOR]**, then you are aware the default colours of **bright yellow and green** for on screen text are rather shocking, and you can't readily change them (for those unfamiliar with this app, read this: [http://ubuntugenius.wordpress.com/2009/12/15/on-screen-display-for-audio-tracks-incoming-emailmessages-in-ubuntu/](http://ubuntugenius.wordpress.com/2009/12/15/on-screen-display-for-audio-tracks-incoming-emailmessages-in-ubuntu/)).

There is a way to change this, by editing a config file:

**sudo gedit /usr/share/python-support/gnome-osd/gnomeosd/server.py**

You will see the following not too far from the top, and the values here are what you need to edit:

[COLOR="#8b0000"]bgcolor = &#8220;**#1B48FF**&#8221;
fgcolor = &#8220;**#6648FF**&#8221;
gosd.BORDER_WIDTH = 1
ANIMATION = True
ANIMATION_STEPS = 10
ANIMATION_TIME = 200[/COLOR]

**bgcolor** is the track name, artist name, album name, and track number (when a compatible audio player like Rhythmbox is running), with the default being bright yellow.

**fgcolor** is the track time after track name, eg: (3:51), as well as the titles &#8220;Artist&#8220;, &#8220;Album&#8220;, and &#8220;Track&#8221; (the default for which is bright green).

However, while the **fgcolor** has changed after a reboot, the **bgcolor** is still yellow, even though its number has been replaced by another. I've tried a couple of different colours and have rebooted, yet only the **fgcolor** changes, and for some reason the **bgcolor** never moves from yellow.

Any ideas as to why this would be? Seems somewhat strange to me. There are 2 other server.py files related to gnome-osd:

/usr/lib/pymodules/python2.6/gnomeosd/server.py
/usr/lib/pymodules/python2.5/gnomeosd/server.py

... but they just reflect the changes made to the other. So I'm at a loss, and could do with some suggestions. Cheers

---

