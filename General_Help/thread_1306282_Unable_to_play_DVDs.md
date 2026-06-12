---
title: "Unable to play DVDs"
date: 2009-10-30
forum: General Help
---

### Post by gigaSproule on 2009-10-30
I can't seem to play DVDs. I've downloaded every codec under the sun and yet I still can't play them. I've even installed VLC, which plays them but the sound is jittery and the video is black, so basically as good as not working at all. If I use totem, it comes up asking me if I have permissions to read it, which I have no clue to sort out, as I've tried using sudo nautilus and then navigating to it and it still won't work.

---

### Post by torger on 2009-10-30
Not sure about the permissions but make sure you have installed dvd playback.  I did a quick search and found this:
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#CDs_and_DVDs](http://ubuntuguide.org/wiki/Ubuntu:Karmic#CDs_and_DVDs)
If you have already installed those packages then I'm not sure what you should do.

---

### Post by grandtoubab on 2009-10-30
Assuming that the package** libdvdread4** is installed (if not do it with Synaptic)

try this it works for me 
**sudo sh /usr/share/doc/libdvdread4/install-css.sh**

Reboot and   ..enjoy :D

Personnally I prefer use the VLC player for DVD and all medias
:popcorn:

---

### Post by gigaSproule on 2009-10-30
You are a genius. Works perfectly with totem and VLC.

---

### Post by grandtoubab on 2009-10-30
Thank you but  I just learned it 3 weeks ago :p
That's how Ubuntu goes:lolflag:

so you can put is as resolved

---

### Post by greyfox1 on 2009-11-05
Just another big THANKS to grandtoubab! I was having issues as well until I ran install-css.sh. Prior to that, I was getting errors like:

> libdvdread: CHECK_VALUE failed
libdvdnav: ifoRead_VOBU_ADMAP vtsi failed

From Totem. I ran the command posted above and playback worked right away, no reboot required!

Hopefully teh googles will pick up on this page, maybe it will save some others from tearing their hair out :D

---

### Post by Rasheeke on 2009-11-07
Just want to add to the pile of thank you's and confirmations that this works.

---

### Post by Paulplex on 2009-11-24
Gotta love forums: I've been playing around with different packages and tweaks for ages before I thought to *search* for an answer.

...doh...

This was the final stumbling block with my move from Windows to Ubuntu: 9.10 is stable, easy to setup and with DVD playback, it's now my replacement to Windows :)

---

### Post by epicoder on 2009-11-24
You could try gxine. The other solution works, but using gxine just seems to work without any fiddling.

---

### Post by snapback77 on 2009-12-23
My thanks to Grandtoubab.  It is great to have a person help another person he doesn't even know.
thanks again.

---

### Post by nchase on 2010-03-04
grandtoubab came through. thank you very much!!! :D

---

### Post by Automat2 on 2010-03-05
Many thanks Grantoubab.

Your patch works for me too!

Edit: It worked even without rebooting.

---

