---
title: "Where is Appearance Preferences"
date: 2011-10-27
forum: General Help
---

### Post by reb68 on 2011-10-27
I have Ubuntu 11.10 and it will not load Google Earth. It worked in the previous Ubuntu. I went to Google earth Help and they list a crashing problem in linux. The workaround is to go to Appearance Preferences and change the Visual Effects to None. I cannot find this . Please help. 
Thank you. :confused:

---

### Post by Frogs Hair on 2011-10-27
Appearance preferences as it was Gnome 2  was removed by Gnome . The effects tab was removed in 11.04 . You will have to find another work around for Gnome 3 . The current version of appearance is found in system settings > appearance .

---

### Post by reb68 on 2011-10-27
Does anyone  know how to get Google Earth to load? I use it very much in the past and would like to get it up and running. I also have WindowsXP on my PC but do not like to move to it. 

Thanks to all

---

### Post by wolfgar on 2011-10-27
This worked for me.

1. Installing google earth in Ultimate Edition 3.2 and destined x32 and x64

> sudo apt-get install lsb-core

> sudo apt-get install googleearth-package

> sudo make-googleearth-package --force

> sudo dpkg -i googleearth<HIT THE TAB KEY> this will allow for the full version to be auto selected

That's It!

If ya need bigger font

 > sudo apt-get install qt4-qtconfig

I hope this helps!

---

### Post by reb68 on 2011-10-27
Well, I did the install as you suggested and it went through a lot of verbage. When I finished I did the last line and TAB . when I went to dash and brought up the GoogleEarth Icon in the Internet file it opened the 1/2 globe foe a few seconds and then closed. It did not open. I do appreciate your effort but it still does the same. If you have any suggestions please let me know. 
Thank You

---

### Post by xianbei on 2011-10-27
don't have a solution for you, but have you tried to update/upgrade?

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Alan.Brown on 2011-10-27
@wolfgar

FWIW - your instructions worked OK for me thanks.  Using Ubuntu 11.10.

Alan

---

### Post by enkay009 on 2011-10-27
If you need to disable visual effects to run Google Earth, then you'll need to logout and login to either "Gnome Classic (no effects)" or "Ubuntu 2d". Neither of these use visual effects.

---

