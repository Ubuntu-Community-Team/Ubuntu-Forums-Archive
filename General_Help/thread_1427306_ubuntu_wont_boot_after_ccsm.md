---
title: "ubuntu wont boot after ccsm"
date: 2010-03-11
forum: General Help
---

### Post by andrew_a72 on 2010-03-11
Downloaded ccsm and was screwing around with some settings to waste time, I enabled desktop cube, everything was working fine, and then I enabled something else, I forget what it was because I was just testing stuff out and after I clicked whatever I did everything stopped responding. So I held the power button to turn off my laptop and now whenever if I try to boot ubuntu it gets to the splash screen, plays the intro sound, and freezes.

Im set up on a dual boot with windows xp (which is what Im using to write post this), Ive thought about booting in safety mode and uninstalling ccsm before ubuntu starts, but I then realized Im not nearly tech savvy enough to do this.

let me know

---

### Post by flippo on 2010-03-11
Boot into recovery mode and get your terminal up.  

Then backup and restore your compiz defaults.  This command will do both at the same time:```
mv /home/<yourusername>/.compiz /home/<yourusername>/.compiz_backup
```

---

### Post by andrew_a72 on 2010-03-16
wont work, says no such file or directory or something along those lines, my username is andrew so i typed

mv /home/andrew/.compiz /home/andrew/.compiz_backup

what did i do wrong

---

### Post by flippo on 2010-03-16
Well, if you don't mind losing your gnome settings (basically anything out of the ordinary you set gnome to do) then you should be able to get away with```
mv /home/<username>/.gconf /home/<username>/.gconf_bup
```You will still encounter an issue if you install compiz again though... to be safe I would move all of these files:

.gconf .gconfd .gnome .gnome2 .gnome2_private .nautilus .themes .local .emerald 

You may not have all of them and moving all of them is most likely not necessary, just try them one at a time until you figure out whats wrong.

---

### Post by andrew_a72 on 2010-03-21
I took my computer to the tech at my school who luckily uses ubuntu and though im not exactly sure what the code he use was it was something to do with

purge ccsm* 
(if you found this post trying to fix your problem, this is not the exact code, but its something like this, ask one of the smarter people)

and now everything is back to normal, more or less. I alt+tab no longer changes windows but I prefer that over ubuntu not booting at all.

Thanks for everyone's help

---

