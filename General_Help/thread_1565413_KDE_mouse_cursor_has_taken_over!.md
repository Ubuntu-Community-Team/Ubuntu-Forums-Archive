---
title: "KDE mouse cursor has taken over!"
date: 2010-08-31
forum: General Help
---

### Post by UncleNinja on 2010-08-31
I installed KDE over Ubuntu using (so I could choose when I log in):
```
sudo apt-get install kubuntu-desktop
```
And now when I log into GNOME my loading and normal mouse cursor is the blobby-lookin KDE one!
I've tried going to System>Preferences>Appearance and customizing my cursor, but no matter what I do the KDE mouse cursor is still there. :o
I use GNOME more than KDE and the mouse is annoying me. I'd rather have my GNOME mouse cursor in both KDE and GNOME than my KDE mouse cursor in both KDE in GNOME (current situation).

I'm using a Compaq Presario CQ60-419wm ($300 laptop from Walmart haha) - [click here for more info on HP's site if you want]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c01753032")

**Model:** Compaq Presario CQ60-419-wm
**Video Card:** Nvidia GeForce 8200M G
**Processor:** AMD Sempron (:frown:) 2.1 GhZ
**RAM:** 3GB
**OS it was shipped with:** Vista Basic (:frown:)

If it helps, when it asked me which X11 thing to use as the default (or something like that) in the terminal (when I installed KDE) I chose GNOME.

Is there any way to get my GNOME mouse back? :confused:

---

### Post by buddyd16 on 2010-08-31
Are you using compiz? 

If so I believe there is a current bug where the X11 cursor theme will only use the default.

---

### Post by UncleNinja on 2010-08-31
> **buddyd16 said:**
> Are you using compiz? 

If so I believe there is a current bug where the X11 cursor theme will only use the default.Yes, I am :KS

At least I have some idea what the problem is. :) Thanks for replying! (no sarcasm intended) :KS

Any other ideas? :)

---

### Post by alem189 on 2010-08-31
This might work for you:

$ sudo update-alternatives --config x-cursor-theme

Select the one you want, then re-login.

---

### Post by M93 on 2010-08-31
try re-installing gnome...this will make the gnome mouse be the default ;)

---

### Post by pithdillinja on 2010-08-31
Try what this page says:

[http://chuckstuff.com/stories.phtml?loadfromfile=tips/Mouse%20Cursor](http://chuckstuff.com/stories.phtml?loadfromfile=tips/Mouse%20Cursor)

I had the same problem. It should work. That's my site, too. Just promoting it a bit. Hope it helps.

---

### Post by UncleNinja on 2010-09-01
> **alem189 said:**
> This might work for you:

$ sudo update-alternatives --config x-cursor-theme

Select the one you want, then re-login.Thanks! That worked! Back to my normal GNOME cursor. :biggrin:

Just for future reference: there's no dash in front of *x-cursor-theme* in that command. :)

Thanks everybody! :KS

---

