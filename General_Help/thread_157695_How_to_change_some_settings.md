---
title: "How to change some settings"
date: 2006-04-09
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-04-09
How can I change how long until my screen turns off and how can I change the time of the admin permissions granted by sudo ?

---

### Post by Ramses de Norre on 2006-04-09
Screen turn off: System > preferences > screensaver > advanced tab and there is a display power management section.
```

 timestamp_timeout
                   Number of minutes that can elapse before sudo will ask for
                   a passwd again.  The default is 15.  Set this to 0 to
                   always prompt for a password.  If set to a value less than
                   0 the user’s timestamp will never expire.  This can be used
                   to allow users to create or delete their own timestamps via
                   sudo -v and sudo -k respectively.
```
I found this in the man page for sudoers, so you need to add a timestamp_timeout line to your /etc/sudoers (and I think you need to put it on the defaults line but I'm not sure.)

---

### Post by stanz on 2006-04-11
[quote=Ramses de Norre]Screen turn off: System > preferences > screensaver > advanced tab and there is a display power management section.
[/quote] Hi All....
Ya know...I always went there also...to disable it all- my choice right!?
Well, after this fresh install...I find the power management section- "set & un-accessable" !???
I cannot find or figure out-also..what i must have done- or downloaded- 
to have set those settings, and lock me out...or 'user' anyway.
ANY direction to pass along?  Thanks- as always!!!!

---

### Post by stanz on 2006-04-12
I had some time to search synaptic, - i think its a laptop power thingy, thats got
my "Display Power Management" - set & not changable, from "screensaver settings".
I've gone thru synaptic- & uninstalled:
[I]toshset, pcmcia-cs, libapm1, apmd, laptop-detect, laptop-mode, hotkey-setup,
gnome-applets.. {so far i've lost 'trash & another icon applets thingy}
[/I]
Also- i found-, which mentioned laptop drivers[I]...
xserver-xorg-driver-neomagic, xserver-org-driver-siliconmotion..[/I]
Which i found out- after removing these, that it broke X11/xserver-xorg.
They got re-installed- by way of: command_line !   :rolleyes:
I don't panic as much-anymore..when xserver brakes...pretty kewl~ I've learnt
some things from here and well,.. i'm here and typing!

Sooo, I'm still wondering WTF....
and wonder also...after the re-install of xorg stuff- i could not:
[I]sudo dpkg-reconfigure -phigh xserver-xorg
[/I]I recieved the post-something warning, about overwritting backup file, which i:
[I]sudo rm /etc/X11/xorg.conf.2006yadda yadda
[/I]but still wasn't permitted to begin reconfigure!? 

Well, this is my latest... I guess I'll re-install the gnome-applets- cause that didn't change any power settings.
Later..!

---

### Post by stanz on 2006-04-12
Alright~~!!
I've re-installed gnome-applets and thats all good. If i remember right- [I]libapm1,
[/I]is a "depends on", package.
Instead of cruizen thru the whole: *dpkg-reconfigure -phigh xserver-xorg *thing-
I went into the */etc/X11/xorg.conf,* file, and made adjustments there- that, 
are from my "printed copy", I'ld made for reference.

I've made the adjustments- i wanted to- for DPM.

---

