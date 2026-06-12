---
title: "Docking video in firefox?"
date: 2006-06-13
forum: General Help
---

### Post by Gividumbuster on 2006-06-13
Hi, I have managed to get all the codecs working using automatix.  Mplayer plays all the streaming videos correctly, the only problem is that it opens a new window and does not play them within the page.  Is there anyway to dock the videoplayer window in the page?

I've searched around for firefox and video, but all the threads have to do with video not playing at all, so that's why I posted this.  Sorry if it's a repost.

Thanks for your help

---

### Post by gr83 on 2006-06-13
Bump.  I've experianced this issue as well and have not found a fix.

---

### Post by JSchwage on 2006-06-13
I'd recommend trying BUMPS instead of Automatix (but that's just me). It installed everything needed to watch videos from within a webpage correctly.

---

### Post by blackjack6.21.91 on 2006-06-13
I've had that happen before.  I think it was when I used automatix.  I would recommend reinstalling the mplayer plugin for mozilla.  That is:
> sudo apt-get remove mozilla-mplayer
sudo apt-get install mozilla-mplayer

---

### Post by Gividumbuster on 2006-06-13
thanks for your replies.

I tried reinstalling the mplayer pluging but it didn't work.
any other ideas?

---

### Post by Gividumbuster on 2006-06-13
I've read around and there is an option in mplayerplug-in.conf called noembed.

for the video to be docked it has to be
noembed=0

the thing is that in my main configuration file (/etc) it is this way, however things do not work.  does firefox use its own configuration file?

---

### Post by gr83 on 2006-06-14
[QUOTE=Gividumbuster]I've read around and there is an option in mplayerplug-in.conf called noembed.

for the video to be docked it has to be
noembed=0

the thing is that in my main configuration file (/etc) it is this way, however things do not work.  does firefox use its own configuration file?[/QUOTE]Was hoping this would be the fix i needed, sadly it wasnt :(

---

### Post by allix on 2006-06-14
This is because you haven't set the video output. While playing a video in your browser, right-click on the empty field in firefox(_not_ the external window that pops up), choose Configure. Set the video output to X11 or xv. It should work now.

---

### Post by bruce89 on 2006-06-14
You could try totem-{gstreamer|xine}-firefox-plugin

---

### Post by Gividumbuster on 2006-06-15
[QUOTE=allix]This is because you haven't set the video output. While playing a video in your browser, right-click on the empty field in firefox(_not_ the external window that pops up), choose Configure. Set the video output to X11 or xv. It should work now.[/QUOTE]

Thank you very much! That was it, I hadn't set a video output!
cheers :D

---

### Post by gr83 on 2006-06-15
[QUOTE=allix]This is because you haven't set the video output. While playing a video in your browser, right-click on the empty field in firefox(_not_ the external window that pops up), choose Configure. Set the video output to X11 or xv. It should work now.[/QUOTE]
Indeed that was the fix.  Simple fix that I'm embrassed I wasn't able to figure it out :-o

---

