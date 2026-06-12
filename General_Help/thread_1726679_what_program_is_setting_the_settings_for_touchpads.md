---
title: "what program is setting the settings for touchpads at startup?"
date: 2011-04-11
forum: General Help
---

### Post by Bladtman242 on 2011-04-11
I'm on a pretty standard ubuntu 10.04 (lucid) install (gnome etc.).
Even though I *am* running x64 I should be surprised if it has any relevance to my problem :)


I am trying to make some changes to the settings for my touchpad.
So far, the  only thing that has worked for me is a bash script that utilises synclient at startup. 
(I have tried xorg.conf, udev and hal/fdi policies without any luck)

Only problem is that at startup, some program resets to the default settings (except for touchpadoff).
Does anybody know which application does this? Because then I could easily alter my bash script to wait until that has been done :)

I hope I'm making myself clear enough, and that somebody knows this :)

---

