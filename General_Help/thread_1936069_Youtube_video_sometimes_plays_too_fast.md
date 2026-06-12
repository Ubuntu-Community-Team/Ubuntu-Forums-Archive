---
title: "Youtube video sometimes plays too fast"
date: 2012-03-05
forum: General Help
---

### Post by Durn Whippersnapper on 2012-03-05
About 1 in every four youtube videos will play too fast. The playing of the video will keep up with how much of the video is actually loaded and the audio will just be static. I think it may be a flash issue, but I've purged and installed flashplugin-installer via apt-get a few times. I'm using chrome on a 64-bit ubuntu 11.10 with xfce 4.8. 

Any ideas about what's going wrong? Thanks

---

### Post by pqwoerituytrueiwoq on 2012-03-05
flashplugin-installer is a dummy package
you want this package instead
adobe-flashplugin
there is a firefox addon called flashvideoreplacer which would bypass your issue if you are viewing on yuotube.com
you may also want to try flash aid (the beta flash has issues with nvidia and youtube and adobe just does not care) 
BTW flash aid affects all installed web browsers

another workaround would be to pause the video and run this long command
```
d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";totem --fullscreen /tmp/"movie-$d"
```
you can change totem at the end to which ever player you prefer eg vlc, mplayer, or smplayer

---

### Post by Durn Whippersnapper on 2012-03-05
I purged flashplugin-installer and installed adobe-flashplugin, and it seems to be fixed. It's a random occurrence though, so I might just be getting lucky. Thanks a lot though!

---

