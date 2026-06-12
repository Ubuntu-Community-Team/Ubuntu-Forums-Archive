---
title: "Looking for somethings [new user]"
date: 2009-12-31
forum: General Help
---

### Post by Mejorado on 2009-12-31
Hey guys, I'm looking for some things for Ubuntu and hoping to enhance my experience..so! lets get started :)

1.) I understand that 'wine-doors' can be used to run Steam, I don't plan on playing games, just to talk to my clan whilst not being on windows is a plus. Does this work on 9.10 release? 

2.) I'm a dock fan, which one would you recommend? and where can I get themes for Ubuntu?

3.) How can I edit GRUB to boot into Windows by default, and change the count-down time?

4.) Anything else you recommend?

-Thank you, and happy new year :D

---

### Post by deadalus.globalnode on 2009-12-31
I would suggest Cairo dock it is my personal favorite, also if you are wanting themes I would get emerald.

---

### Post by Mahngiel on 2009-12-31
1.) *shrug* check the winehq database
2.) Cairo-dock is popular, as is Avant Window Manager
3.) sudo gedit /etc/default/grub

```

GRUB_DEFAULT=saved  [COLOR=Blue]1.[/COLOR]
GRUB_HIDDEN_TIMEOUT=4 
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT="-1" [COLOR=Blue]2.[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```[I]1. This is the auto highlighted selection at grub boot.  It can be any integer to represent the order in which your preferred selection is chosen, which will depend on what order and how many kernels/options you have. Or 'saved' to be the last you used.
2.  This is the amount of time you have to make your own selection.  Any number will represent the seconds to elapse before auto-selection, or -1 will make it sit still until you choose.[/I]
**Note:** you _must_ sudo update-grub in order for this to take affect

4.) Like what?

---

### Post by danastasio on 2009-12-31
Gnome-do is by far my favorite dock!!

[http://www.gnome-look.org](http://www.gnome-look.org) has an amazing collection of themes stuffs.

I dont really rec. anything else. Almost all of the software that comes with ubuntu is all you'll ever need. however

```
sudo apt-get install simple-ccsm
```

will make things all nice and pretty!

(and bouncy)

Rock on!
:guitar:

---

### Post by Mejorado on 2009-12-31
Brilliant :) thanks you all. I'm looking at the docks now all seem pretty cool, changing Grub looks easy enough... oh, and one last question, are themes universal? or are they specifically tied to releases, eg. 8.04, 9.10?

---

### Post by feelshift on 2009-12-31
An easy way to edit grub is by installing Startup-Manager
```
sudo apt-get install startupmanager
```
After that you can find it in System -> Administration :)

---

### Post by Mejorado on 2009-12-31
> **feelshift said:**
> An easy way to edit grub is by installing Startup-Manager
```
sudo apt-get install startupmanager
```
After that you can find it in System -> Administration :)

even better :) thanks!

---

### Post by Mahngiel on 2009-12-31
they're tied to the environment you are using. If you use gnome, then KDE, icewm, or any other the other various DEs themes won't work.

---

