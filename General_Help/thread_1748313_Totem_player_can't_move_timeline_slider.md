---
title: "Totem player: can't move timeline slider"
date: 2011-05-03
forum: General Help
---

### Post by imbjr on 2011-05-03
I thought I heard a glitch in an mp3 I was playing, so I decided to replay the previous 30 seconds or so of the track, only to discover that I can't move the time-line slider, paused or unpaused.

Anyone else with this?

---

### Post by Lateralis on 2011-05-03
Someone else reported this very problem very recently (over the weekend).  I can't remember the exact solution unfortunately, but if you search the forums you should quickly find it.

Edit: In fact, I've saved you the bother of searching.  Have a look [here]("http://ubuntuforums.org/showthread.php?t=1745673&highlight=totem+mp3") and follow the link therein.

---

### Post by imbjr on 2011-05-03
> **Lateralis said:**
> Someone else reported this very problem very recently (over the weekend).  I can't remember the exact solution unfortunately, but if you search the forums you should quickly find it.

Edit: In fact, I've saved you the bother of searching.  Have a look [here]("http://ubuntuforums.org/showthread.php?t=1745673&highlight=totem+mp3") and follow the link therein.

Thanks, that did the trick.

---

### Post by alexsmith on 2011-05-11
For the impatient, the link above takes you to this (which solved my problem too):

```
sudo apt-get remove gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
sudo apt-get install gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-plugins-mp3-partner

```

BTW, I'm running Ubuntu 11.04 - the Natty Narwhal.

Thanks a lot!

---

