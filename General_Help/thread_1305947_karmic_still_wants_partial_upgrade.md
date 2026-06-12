---
title: "karmic still wants partial upgrade"
date: 2009-10-30
forum: General Help
---

### Post by sdowney717 on 2009-10-30
i was hoping it would be resolved for me.
running it since alpha6
should i go for it?

---

### Post by phillw on 2009-10-30
> **sdowney717 said:**
> i was hoping it would be resolved for me.
running it since alpha6
should i go for it?


::GULP::

I would go for it, but that is just MHO - The screen-shot shows a couple of possible issues. I'd let it do it, then re-try & see if it will tell you what it is unhappy with.

But, I can't guarantee we won't break something along the way.

Phill.

---

### Post by Monotoko on 2009-10-30
i had that problem a few days ago, i tried the partial upgrade but it failed, i updated to the full version using the following:

```
sudo aptitude update
```

```
sudo aptitude safe-upgrade
```

and then it worked :)

---

### Post by sdowney717 on 2009-10-30
it may have been mplayer 

> scott@scott-desktop:~$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
The following packages have unmet dependencies:
  mplayer-skins: Conflicts: mplayer-skin-blue (< 3) but 1.6-2 is installed and it is kept back.
scott@scott-desktop:~$ sudo apt-get remove mplayer-skin-blue


> scott@scott-desktop:~$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
The following packages have been kept back:
  gstreamer0.10-plugins-bad libpulse-browse0 libpulse-mainloop-glib0 
  libpulse0 pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth 
  pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11 
  pulseaudio-utils ubuntu-desktop 
The following NEW packages will be installed:
  libpst4{a} linux-headers-2.6.31-14{a} linux-headers-2.6.31-14-generic{a} 
  linux-image-2.6.31-14-generic{a} xserver-xorg-input-mouse{a} 
  xserver-xorg-input-vmmouse{a} 
The following packages will be upgraded:
  evolution-plugins linux-generic linux-headers-generic linux-image-generic 
  xserver-xorg-input-all 
5 packages upgraded, 6 newly installed, 0 to remove and 12 not upgraded.
Need to get 39.4MB of archives. After unpacking 173MB will be used.
Do you want to continue? [Y/n/?] y


---

