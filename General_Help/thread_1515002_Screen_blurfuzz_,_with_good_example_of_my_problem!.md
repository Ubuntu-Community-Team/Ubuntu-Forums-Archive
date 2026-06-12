---
title: "Screen blur/fuzz , with good example of my problem!"
date: 2010-06-21
forum: General Help
---

### Post by rsala004 on 2010-06-21
Just recently installed Ubuntu onto my desktop computer and for some reason all the text seems very odd and fuzzy, it hurts the eyes.  It is not only the text that is bad , even the cursor looks somewhat off..

If I actually inspect the images and letters I notice what is wrong, everything has a "GHOST" shifted 1 or 2 pixels to its right, I do not understand..

I have updated to current nvidia drivers through "hardware drivers" tool, but no change..

my version is lucid lynx, anyone have any ideas?

heres an example to describe a bit more:


Heres what a normal box should look like:

[IMG]http://img34.imageshack.us/img34/9638/normale.png[/IMG]

Heres something like what I see, i get a 'ghost' image shifted a bit to the right.. causing a blur effect,
.. imagine this everywhere , the cursor, every font character, every image .. etc..  its even straining on the eyes as I type this
[IMG]http://img267.imageshack.us/img267/5696/whatisee.png[/IMG]

any ideas?

[SIZE=4]THANKS FOR HELPING[/SIZE]!

some additional details:
19in monitor (4:3)
using 1280x960 res (4:3) , which appears normal in windows.
the blur/fuzz effect decreases when lowering resolution to 1024/786 but not completely gone.. this resolution is not very usable though.

---

### Post by acrazyplayer on 2010-06-21
Its not letting me see your pictures but we could try a few things to see if it gets fixed. First try seeing if there is anything on your monitor that you may have changed or perhaps you can reset it back to factory defaults, second you could try a different monitor if possible. 

Things inside Ubuntu you could try is going to "System/Preferences/Apperance" and then going to the fonts tab. There I would try changing just about everything to see if anything makes a difference.

To be honest it sounds like a refresh rate problem so you could try typing into a terminal "gksudo nvidia-settings" and looking for something that may be of use.

---

### Post by rsala004 on 2010-06-24
Still can't find solution  :(

---

