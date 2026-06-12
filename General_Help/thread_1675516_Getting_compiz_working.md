---
title: "Getting compiz working"
date: 2011-01-25
forum: General Help
---

### Post by Scooter_X on 2011-01-25
So I just installed 10.10 on my wife's laptop. A laptop that is totally capable of handling compositing effects. However I used a liveUSB of 10.10 netbook edition, just because I had already been using it to get a couple of netbooks up and running. I figured that it was the same thing as 10.10 desktop edition, except for one included the netbook interface and the other did not. But I now think that there's more differences than just that. I thought that my little netbook didn't do compositing effects because the OS detected that the hardware was not quite what was needed, but now I think that it is because the netbook edition is set up differently for less powerful systems.

So, I spent a good while getting things up and running, getting files transferred over, etc. I could just install 10.10 desktop from scratch to get it, but I'm wondering if anyone knows how to get compiz up and running.

I've installed the 'compiz icon' and the package 'compiz' but don't get any effects, my 'effects' tab under 'appearances' still has all options grayed out, etc. At this point I don't know what else to do... Any ideas? Thanks. 

(Sorry for having to make you read an entire novel)

---

### Post by corncob on 2011-01-25
Did you install compizconfig-settings-manager?

---

### Post by Scooter_X on 2011-01-25
> **corncob said:**
> Did you install compizconfig-settings-manager?

yes. the 'Advanced Desktop Effects Settings (ccsm)' one. Also I noticed within the manager that I don't even have options for 'expo' and probably some others. From what I remember there were many more options than what is there now. 

Another thing I just realized as I sit here at work and look at the packages that come up when I type in 'compiz' in the software centrer is that there are two that could be it. I'll attach a screenie to help describe.

Package '1' (in the screenie) didn't show up on my wife's when I was looking, so I installed package '2'. I don't know what the difference would be.

---

### Post by Frogs Hair on 2011-01-25
Have you installed the proprietary driver needed to run 3D effects from the additional drivers jockey ?

---

### Post by ajgreeny on 2011-01-25
UNE does not install compiz, if I remember correctly, so your ccsm will be useless, unless, of course compiz was a dependency of ccsm, which surprisingly, it doesn't appear to be.  I see you have installed compiz, however, but wonder if there are still missing packages.

The easiest way to go now is just to run ```
sudo apt-get install ubuntu-desktop
```which will turn your UNE into a standard ubuntu system, plus the UNE packages that would not normally be installed.  Or you can install the missing packages that you want one by one.

This is, in fact, how I have installed both 10.04 and 10.10 to my desktop machine, having D/L'd the iso for UNE first for netbooks.

---

### Post by Scooter_X on 2011-01-25
> **ajgreeny said:**
> 

The easiest way to go now is just to run ```
sudo apt-get install ubuntu-desktop
```which will turn your UNE into a standard ubuntu system, plus the UNE packages that would not normally be installed.  Or you can install the missing packages that you want one by one.

This is, in fact, how I have installed both 10.04 and 10.10 to my desktop machine, having D/L'd the iso for UNE first for netbooks.

That sounds like a dang good idea. I'll try it when I get back home.

EDIT: Yeah! It worked. Thanks a ton. I didn't see it at first though because nothing happened. (I was already running in desktop but without compiz) And then I went and changed visual effects to 'normal' and I was up and running. Woot woot!

---

### Post by Scooter_X on 2011-01-26
Wait, time out. Every time I start up the computer I get no window decorations until I reset metacity. And if I set my decorator to compiz (using the compiz fusion icon) instead of metacity, the decorations disappear. ...?

EDIT: Also I had to go back and turn on visual effects again once I started it up this morning. Like none of my settings stuck.

---

### Post by ajgreeny on 2011-01-26
Open up ccsm and go to the Window decoration plugin.  In that check that you have the command /usr/bin/compiz-decorator in the command box.

Now in System ->Preferences ->Startup Applications add an entry for Compiz with the command **compiz --replace** in the box.

---

### Post by IWantFroyo on 2011-01-26
You can't edit compiz solely with only the compiz package. Open marketplace and search ccsm. Get configure compiz with compizconfig. Then you should be able to edit animations.
Tip: when adding an animation, your Windows Match should be just: normal.
Edit: beaten to it. =D

---

### Post by Scooter_X on 2011-01-26
Well, I already had ccsm installed, and the window decorator line was telling me that it was trying to use the KDM decorator. Random. Anyway, I told it to go back to whatever default was and it replaced that line with just what ajgreeny suggests. That didn't take either. Kept trying many different things, but at this point I've installed Emerald and replaced that infamous line with 'emerald --replace' and now I'm OK. And the title bars are even flashier! :D

Thanks. I don't know why that other method didn't work. But I found a workaround.

---

