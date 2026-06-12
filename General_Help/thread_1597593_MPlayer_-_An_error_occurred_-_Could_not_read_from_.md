---
title: "MPlayer - An error occurred - Could not read from source"
date: 2010-10-15
forum: General Help
---

### Post by Quackers on 2010-10-15
My system is playing CD's fine but I just tried a DVD (non-BluRay) and I get that error!
I have googled about and though I already had the ubuntu-restricted-packages I didn't have all the gstreamer0.10plugins-bad installed (as seems to be the recommended fix). I now have them and MoviePlayer still gives the same error. 
I also want BluRay's to be playable and I was investigating that when I thought I would check whether normal DVD's were still working (I'm not sure whether I've tried a DVD since I upgraded to MM).
Good job I did :-)
The DVD mounts ok and appears on my desktop with the title.
Any assistance would be very nice :-) Thanks

---

### Post by dino99 on 2010-10-15
a quick search:

you need libbluray installed

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

[http://stream-recorder.com/forum/play-blu-ray-video-ubuntu-9-10-t4993.html?](http://stream-recorder.com/forum/play-blu-ray-video-ubuntu-9-10-t4993.html?)

maybe lxBDPlayer can help too

---

### Post by Quackers on 2010-10-15
Thanks for that dino99, but I'm struggling to get normal DVD's running at the moment :-)
(I'd installed MakeMKV before I tried the normal DVD's, so I've made a start on BluRay stuff).

---

### Post by Quackers on 2010-10-15
I'm a bad boy :-(
I forgot there is a Multimedia forum here. I've been there and run everything in the Sticky and now normal DVD's are working fine.
I should have remembered before asking silly questions.
Apologies.
I'm playing with MakeMKV and BluRays now :-)
I'll be looking at your links dino :-)

---

### Post by Quackers on 2010-10-15
Just as an update and for future readers I seem to have stumbled my way through to getting BluRay discs playing with Movie Player, via MakeMKV.

---

### Post by treerink on 2011-03-22
If you have, like me, with certain DVD's for Media Player (mplayer) the message:
 An error occurred - Could not read from source
and similar for VLC, Then this solves it (in the Terminal): 
 sudo /usr/share/doc/libdvdread4/install-css.sh
and eventually before:
 sudo apt-get install libdvdread4
if it is not present

(see e.g. [http://ubuntuforums.org/archive/index.php/t-1137655.html](http://ubuntuforums.org/archive/index.php/t-1137655.html))

---

