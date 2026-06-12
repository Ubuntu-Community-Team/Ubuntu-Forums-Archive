---
title: "gdm interfering with nvidia-settings additional screens?"
date: 2010-11-02
forum: General Help
---

### Post by t.rei on 2010-11-02
Hi,

after many a tear I just by sheer chance found out that, when logging in to my gnome-session (or any session really) from kdm I can do something that has eluded me for quite a while now: change screen-configuration between 1 screen and 2 screens as I please without having to log out, shutdown x, copy xorg.conf I need, restart x, log back in. 

:popcorn:

So question is: what could it possibly be, that makes GDM break a feature like this for the nvidia-settings dialog? Can anyone confirm this? 
*wants that error and shoot it in the face... er... code!* 

I still don't feel like reinstalling the whole thing, just to find out if this is due to this system being... well... OLD. Also call me a bit oldschool, but reinstalling is just lame. :P

*edit* me dumbass:
NVIDIA-Linux-x86-260.19.12.run
2.6.35-23-generic-pae
maverick

---

### Post by t.rei on 2010-11-02
Update on my quest to solve the riddle:

When I started ubuntu-tweak in the kdm -> gnome session it tells me "this is only available in gnome-desktop environment" (well in german, so something along those lines). I guess something that gdm does that makes this a gnome session might also be related to the 'only garbled junk when switching screens' issue.

---

### Post by t.rei on 2010-11-07
Another update - I'll edit the title afterwards:

It's not gdm, it **compiz**!

solution for me now:
If I want to change screen layout, I must use metacity --replace before running nvidia-settings, and compiz --replace afterwards. Then it works.

---

