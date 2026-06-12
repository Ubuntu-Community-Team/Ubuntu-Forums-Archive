---
title: "DVD plays autdi but not video."
date: 2010-01-09
forum: General Help
---

### Post by llawwehttam on 2010-01-09
Just tried to play a dvd and the audio is fine but the video is just black. Its the same for any video regardless of format.

The only thing I have done recently is to install the latest nvidia drivers for my graphics card.

Totem and VLC both are black and MPlayer gives the error:

Fatal error!
Error opening/initialising the selected videeo_out(-vo) device

Any help appreciated.

EDIT: mispelt in the title. It should say "DVD plays audio but not video"

---

### Post by llawwehttam on 2010-01-09
After changing the vo_driver line in ~/.mplayer/gui.conf to:
```
vo_driver = "x11"
```
mplayer works. I would really like to get the others working too though.

---

### Post by llawwehttam on 2010-01-09
Update:
I now have got vlc working by changing the output in the video tab to x11 instead of default.

Is there a similar setting in totem as I can't find one.

---

### Post by llawwehttam on 2010-01-09
Update:


ITS FIXED!!!!!!!!!

I ran the command ```
sudo apt-get purge totem*
```
then made a note of everything it removed and then ran 
```
sudo apt-get install (everything it removed)
```

Now all is back to normal

---

### Post by ajgreeny on 2010-01-09
To change this in totem I think you probably need ```
gstreamer-properties
``` in terminal, though this assumes you are using the default gstreamer version of totem, and have not changed to totem-xine.

EDIT:
While I was typing this you solved the problem.  Do you know which vo driver you are now using in totem, or are you just happy that it all works now?

---

### Post by llawwehttam on 2010-01-09
To be honest I'm just happy it works now. Gstreamer-properties would have worked as well looking back.

Thanks anyway.

---

