---
title: "Compiz problem"
date: 2010-05-02
forum: General Help
---

### Post by DeMus on 2010-05-02
Hi, I installed Compiz and most of the effects I switched on work, except Windows previews. As you can see on the attached picture, I did switch it on, place the mouse on one of the two program buttons in the panel but no Window Preview.
Is there something else I need to install or configure for this?
I run Ubuntu-Studio 10.04 - 64.

---

### Post by akand074 on 2010-05-03
hmm.. no it should work fine. Do you have any docks running? because sometimes the windows preview only works with the dock and other times only from the panel. Though it looks like you don't have a dock unless you don't put it at the bottom of your screen. Do all the rest of your compiz effects work?

---

### Post by WorMzy on 2010-05-03
What settings are you using. Here's a screenshot of mine, which works, for comparison.

[[IMG]http://www.ubuntu-pics.de/thumb/55917/desk_1_090_Zkf7Ya.png[/IMG]]("http://www.ubuntu-pics.de/bild/55917/desk_1_090_Zkf7Ya.png")

What I have installed:
compiz, compiz-plugins, compiz-gnome, compiz-core, liemeraldengine0, emerald, compiz-fusion-plugins-main, compiz-fusion-plugins-extra, compizconfig-back-end-gconf

---

### Post by bigsmitty64 on 2010-05-03
One thing I've noticed is that they only work when the window is open, and NOT when they are minimized, which I think should be the opposite.

---

### Post by WorMzy on 2010-05-03
It works when windows are maximised for me..

---

### Post by DeMus on 2010-05-03
> **akand074 said:**
> hmm.. no it should work fine. Do you have any docks running? because sometimes the windows preview only works with the dock and other times only from the panel. Though it looks like you don't have a dock unless you don't put it at the bottom of your screen. Do all the rest of your compiz effects work?

Thank you for answering. I don't use any docks so that can't be it. Other Compiz features do work, although I don't use many of them. I use animations and Wobbly Windows which just look nice.
When I installed Compiz it said I needed some extra packages as well which I also installed. Should there be more I need to install? Which Compiz packages did you install? Mine are in the attached picture.

---

### Post by DeMus on 2010-05-03
> **WorMzy said:**
> What settings are you using. Here's a screenshot of mine, which works, for comparison.

[[IMG]http://www.ubuntu-pics.de/thumb/55917/desk_1_090_Zkf7Ya.png[/IMG]]("http://www.ubuntu-pics.de/bild/55917/desk_1_090_Zkf7Ya.png")

What I have installed:
compiz, compiz-plugins, compiz-gnome, compiz-core, liemeraldengine0, emerald, compiz-fusion-plugins-main, compiz-fusion-plugins-extra, compizconfig-back-end-gconf

I only use a smaller size border but the rest is the same. I do not have emerald installed nor the extra plugins. The last one doesn't want to be installed because of dependencies which don't want or can't be installed. It depends on Depends: compiz-core-abiversion-20090619 and that one won't be installed.

---

### Post by WorMzy on 2010-05-03
Strange, mine doesn't list that as a dependency.. but I don't think it'd make any difference here anyway. You won't need emerald unless you want to use it as a window manager. I don't think installing plugins-extra will help, since that doesn't contain anything relating to window preview. So the only other thing I can think of is: maybe there's a conflict with ubuntu-tweak? I don't even have that in my repositories, so I can't test whether mine works with it.

---

### Post by DeMus on 2010-05-03
> **WorMzy said:**
> Strange, mine doesn't list that as a dependency.. but I don't think it'd make any difference here anyway. You won't need emerald unless you want to use it as a window manager. I don't think installing plugins-extra will help, since that doesn't contain anything relating to window preview. So the only other thing I can think of is: maybe there's a conflict with ubuntu-tweak? I don't even have that in my repositories, so I can't test whether mine works with it.

Okay, thanks again for your answer. I will study Ubuntutweak this evening when I'm home again. I will let you know if I can find something.
Btw, the dependency I was talking about is not for Emerald but only for the Compiz-Extras.
I do run Ubuntu-Studio Lucid and maybe this works a bit different from the "normal" Ubuntu.

---

### Post by DeMus on 2010-05-03
Well, I am home and found something very strange:

I do get the Windows Previews when .... Ubuntu Tweak is running. I found another thread with the same problem and there they said in Ubuntu Tweak I had to switch on: Show Desktop Icons. This was set on already but when I placed the cursor on top of the buttons in the lower panel I got my previews. The moment I stop Ubuntu Tweak they don't appear any more. I didn't have to change something, the fact whether that program is running is enough.
What can cause this? Why is it like that?

---

