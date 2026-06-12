---
title: "Buggy activation of screen saver in Karmic"
date: 2010-01-04
forum: General Help
---

### Post by teachmeifyoucan on 2010-01-04
Hi,

my Karmic installation has two problems regarding screen saver activation:

1) VLC is set to deactivate the screen saver during playback, but the screen saver activates anyway.

2) Sometimes, when NOT running VLC, the screen saver doesn't activate itself at all. I've set it to 5 minutes, but after 5 minutes of inactivity, nothing happens. This ALWAYS occurs while running a java web applet, and SOMETIMES also occurs when no software is running at all.

I've googled this to death, but can't find any information relevant to this problem. Thanks for your help.

---

### Post by Jenkins1 on 2010-01-04
The vlc not disabling the screensaver is a known bug [https://bugs.launchpad.net/ubuntu/karmic/+source/gnome-screensaver/+bug/428884](https://bugs.launchpad.net/ubuntu/karmic/+source/gnome-screensaver/+bug/428884)
I got the package 2.28.0-0ubuntu3.2 (in the last post in the bug) in an update today I haven't tried it but it should be fixed.

---

### Post by teachmeifyoucan on 2010-01-04
Hi,

thanks for your quick response.

The discussions at bugs.launchpad.net have always been gibberish to me. How exactly do I install this patch?

---

### Post by Jenkins1 on 2010-01-04
just go system > administration > update manager and check for updates it should be in the list there. It was for me today. to get it just apply updates as normal.

---

### Post by teachmeifyoucan on 2010-01-05
My system appears to be up-to-date. However, the VLC bug persists.

---

### Post by karmakowski on 2010-01-17
> **teachmeifyoucan said:**
> Sometimes, when NOT running VLC, the screen saver doesn't activate itself at all. I've set it to 5 minutes, but after 5 minutes of inactivity, nothing happens. 

I have the same problem. Is there any information on that? Maybe a way to debug? 
It's a quite serious security flaw.

---

