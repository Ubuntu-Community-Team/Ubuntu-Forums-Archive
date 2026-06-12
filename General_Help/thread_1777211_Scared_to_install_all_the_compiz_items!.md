---
title: "Scared to install all the compiz items!"
date: 2011-06-07
forum: General Help
---

### Post by soiled skivvies on 2011-06-07
I just got upgraded to 11.04 and everything is absolutely beautiful and crystal clear.  For the first time, I can really SEE my monitor, even the fonts... you can zoom down to the pixel and it still looks good... 

Now I know it uses (some) compiz libraries or whatever you call it.  The update manager (set for end user and only check proposed once a week manually) brought up Compiz-everything pretty much.  Now here's where it gets scarey for me....

I have been virtually married to Ubuntu, and now that my Direct Rendering WORKS..with my ATI 4850HD... I read basically everywhere compiz turns off direct rendering and you have to do a bunch of uninstall commands...(meant to fix but) which completly disables the system EVERYTIME, I get stuck with a shabby, nasty looking crap monitor (after hours of yelling and screaming) and not even the most basic Gnome program will even run without a seemingly endless loop of errors and system lockups (yet nightly firefox is flawless)... 

Now the real question (I ramble, but wanted to be very specific).
Is it at all within even a remote possibility to keep all Compiz effects and animations (because it's beautiful) AND keep my direct rendering 100% of the time without errors as it currently runs? ...OR...Find out which compiz effects/settings disable direct rendering so I can avoid them?

---

### Post by seawolf167 on 2011-06-07
I couldn't tell you which Compiz settings would mess around with your display, but what I can suggest is making a backup image of your hard drive using [Clonezilla]("http://www.clonezilla.org"), then installing Compiz and turning on the settings one at a time to see which (if any) produce negative results, then turning those off (the negative ones) and moving on to the next setting. If you get stuck and can't figure out how to return to your "perfect" setup, simply restore the hard drive image you made with Clonezilla and you are back to the way it was, pre-compiz settings as if nothing ever happened.

---

### Post by soiled skivvies on 2011-06-07
Thanks! I'll give it a try!

---

### Post by seawolf167 on 2011-06-07
Report back if you do find any Compiz settings that don't work for you - then anyone else wondering the same thing can see what you found out

---

### Post by Irony on 2011-06-07
```
sudo cp -ax /. /media/backupdrive/backupfolder/.
```

---

### Post by soiled skivvies on 2011-06-09
I'm guessing that command will make an entire copy of my monstrosity of a hard drive?
  Well, I would LOVE to test all the compiz setting and report back with my findings, but,... How do I turn Direct Rendering back on once it's off? disable the addon I tried and reboot?

---

