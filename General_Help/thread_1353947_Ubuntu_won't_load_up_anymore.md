---
title: "Ubuntu won't load up anymore"
date: 2009-12-13
forum: General Help
---

### Post by xZachtmx on 2009-12-13
I am using ubuntu 9.10 and it has worked fine until now.  While I was installing some sdl libraries for a game the extraction program stopped working so I used the terminal but I noticed no other program would start either, so I restarted my computer and I selected the ubuntu kernel it went to the loading screen and it even went to the desktop but the GUI started flickering making it unusable so I reset again and went into restore mode and repaired broken packages but now the GUI doesn't even load, just a movable loading cursor on a black background that would not go away after 8 hours.  I tried all 3 ubuntu kernels and the same thing happens.  I don't want to do a fresh install as I have slot of libraries so any help is greatlyappreciated !

---

### Post by Daveth on 2009-12-13
you might want to try

```
sudo /etc/init.d/gdm restart
```

if you are/ were using gnome. It will restart the gnome desktop- sounds like it has not loaded. I think the KDE version is kdm, but check!

---

### Post by xZachtmx on 2009-12-13
Thanks for your reply!  I went into the recovery mode terminal and typed I in but it said this : 

Rather than invoking initial scripts through /etc/init.d, use the service(8) utility, eg service gdm restart

since the script you are attempting to invoke has been converted to an upstart job, you may also use the restart(8) utility, eg restart gdm gdm start/running, process 1236.

What does all this mean?

---

### Post by xZachtmx on 2009-12-13
Ok I got it to reset but nothing was fixxed.  I also found out that dpkg-reconfigure xserver-xorg doesent let me configure xorg and it dosent even give me the option to in recovery mode anymore.  I was using the open source Ari drivers which worked(not very well) up until now.  I am stumped so thanks to any help I hope I can get this fixxed tonight :S

---

### Post by Daveth on 2009-12-13
ah, new fangled operating systems. Another posts suggests that Upstart is handling the loading of the desktop rather than the init.d process, so gets hacked off if it is pushed out of the way. The post suggests:

```
sudo service gdm start
```

so try that!

---

### Post by xZachtmx on 2009-12-13
Huh, it Says it is already running :o

---

### Post by xZachtmx on 2009-12-13
Could my problem be gnome is failing?  Maybe that's why only a cursor and a flickering white box on a black screen spear  ;?  Does anyone know how I can reinstall gnome or whatever?  Thanks!

---

### Post by xZachtmx on 2009-12-13
Here is what happens now when I type sudo gdm restart:

```
(gdm-binary:2318) WARNING : failed to aquire org.gnome.DisplayManager
```

---

