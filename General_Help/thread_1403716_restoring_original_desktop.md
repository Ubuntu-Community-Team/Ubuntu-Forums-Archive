---
title: "restoring original desktop"
date: 2010-02-10
forum: General Help
---

### Post by ss3000 on 2010-02-10
hello, i'm new to ubuntu and so far am liking the flexibility it has to offer!! but i've come across a hitch. as i was originally a windows user, i opted to install a windows 7 transformation pack, using some help from youtube i installed most of the theme. but had problems installing dockbar X.

anyway now i dont know how to install dock bar x, i found the terminal info for it in these fourms but i dont think i did it correctly, when ever i add dockbar it appears as a thin white line on my panel. 

also i think this theme is slowing my PC down alot, in general ubuntu is surprisingly slow ( :( ) on my computer (its old - amd xp 2400+, 512mb ram.....) so i want to get rid of the windows these and go back to the default theme that was on the desktop after installing ubuntu.

please can someone help.

sorry for being so comprehensive.

---

### Post by testtubeunicorn on 2010-02-10
You might  want to consider a fresh install.  The first time I switched to linux from windows I installed and reinstalled at least four times before I got it right...  It's a learning experience.

Edit:  If your hardware isn't sufficient, try some of  the lighter linux distributions, like ones that include xfce or lxde as desktop environments, which tend to be much lighter than gnome.  (Although, note that I use ubuntu and gnome on my netbook, so it's up to your preference.)

---

### Post by oshunluvr on 2010-02-10
If you just want to restore your original desktop - rather than a total re-install create a new user. This will give you a new but original desktop.

Good idea to have a "spare" user account to try new things with anyway.

---

### Post by Sef on 2010-02-10
This might help

```
sudo apt-get update

sudo apt-get install ubuntu-desktop
```

---

### Post by Megafag on 2010-02-10
> **testtubeunicorn said:**
> Edit:  If your hardware isn't sufficient, try some of  the lighter linux distributions, like ones that include xfce or lxde as desktop environments, which tend to be much lighter than gnome.  (Although, note that I use ubuntu and gnome on my netbook, so it's up to your preference.)

[Crunchbang]("http://crunchbanglinux.org/") is a pretty good one.

---

### Post by paul_in_london on 2010-02-10
See if this thread helps:

[http://ubuntuforums.org/showthread.php?t=419162](http://ubuntuforums.org/showthread.php?t=419162)

---

### Post by ss3000 on 2010-02-11
thanks for all the replies!! after writing that post i turned off my computer and turned it back on 2 hours later, and it was back to the original desktop, no sign of any transformation packs being applied. its definately running more smoothly now, no lags when opening up a programme or the application menu.

before posting on this forum i googled how to restore my desktop and typed in: 

rm -r .gnome .gnome2 .gconf .gconfd
into the terminal, but it did nothing at the time. oh well i'm not complaining, just glad its back to normal.

thanks for the advise i'll open up another account just to try out things until i get more confident in using linux to a greater potential.

also is my computer really slow for ubuntu 9.10? i've had previous versions installed before just as a back up OS but my wireless mouse wouldn't work (the keyboard did and still does though!!). 

i'm using an AMD athlon XP2400+ (2.0 Ghz process, just single core)
512 MB ram (497.8MB)
 
its what i was using windows XP on, and that worked with out any problems. always thought that ubuntu would be less resource hungry and be more efficient and stable than XP.

---

