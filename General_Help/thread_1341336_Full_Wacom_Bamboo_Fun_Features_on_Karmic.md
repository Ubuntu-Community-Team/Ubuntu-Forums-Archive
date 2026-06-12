---
title: "Full Wacom Bamboo Fun Features on Karmic?"
date: 2009-11-29
forum: General Help
---

### Post by higashi on 2009-11-29
I've had my Wacom Bamboo Fun tablet for quite a while and haven't really used it to it's full potential. While in Jaunty, i was able to use pressure sensitivity, configure buttons, scroll wheel, etc. But, now that i've upgraded to Karmic, I have no idea how to do anything.

I've been to the wiki, but it doesn't seem to say anything about Karmic, and i've checked other posts, but still no luck.

Can someone please tell me how i can configure the scroll wheel, pressure, & buttons?

---

### Post by ranch hand on 2009-11-29
This thread will probably help;

[http://ubuntuforums.org/showthread.php?t=967147](http://ubuntuforums.org/showthread.php?t=967147)

Yes it has been around awhile.  Check toward the end of the bugger where it is fresh.

---

### Post by higashi on 2009-11-29
woah, looks like im gunna have a lot of reading to do. I'll post back here once i've decided i have the time. x]

EDIT: That guide didn't work. When i go to edit my xorg.conf, i get a blank text document. ):

---

### Post by Favux on 2009-12-01
Hi higashi,

You don't want to use xorg.conf in Karmic.  Instead you want a wacom.fdi.  See the explanation and instructions in [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").  Then you can follow "shatterblast's post #188 on the following page".  He shows you how to set up the pad for a Bamboo.

---

### Post by higashi on 2009-12-02
It worked! Thanks a bunch!
The only thing im having trouble configuring is the scroll wheel. if i go counterclockwise, it scrolls up, but clockwise doesn't seem to do anything...
my pad configurations are as follows:

button 1: left
button 2: middle
button 3: right
button 4: fourth
Ring Anticlockwise: fourth
Ring Clockwise: fifth

---

### Post by Favux on 2009-12-02
Hi higashi,

Great!  You're welcome.

The scroll wheel may or may not be fixable.  There are other folks dealing with it on the Wacom thread the .fdi is on.  You could search the thread.

You can also look at the LWP's HOWTO.  It has examples of commands for the pad.  It's [here]("http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom").  You'd modify the .xinitrc of wacomcpl.

---

### Post by higashi on 2009-12-02
ok, thanks again. (:

---

