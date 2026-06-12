---
title: "Unable to find package"
date: 2009-08-01
forum: General Help
---

### Post by walkerx on 2009-08-01
I've just updated my system and lost the x-fi sound, which i've now resolved following a thread on these forums.

But the issue I had was trying to download the flash plugin using the command:

sudo apt-get install flashplugin-nonfree-extrasound

but this returned the following error

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree-extrasound

I've tried sudo apt-get update, and then the above again but exactly the same.

Is there anything else I need to do?

thanks in advance

---

### Post by darkhammer8108 on 2009-08-01
i think your looking for:
```
sudo apt-get install flashplugin-installer
```
alternatively you could install the medibuntu repo and just get every codec u will ever need from the package 'non-free-codecs' which depends on everything that gives u a codec.

---

### Post by credobyte on 2009-08-01
You need to enable multiverse repositories ;)

---

### Post by Tclarkie on 2009-08-01
[I]here is the .deb  
[http://rapidshare.com/files/155584596/install_flash_player_10_linux.deb](http://rapidshare.com/files/155584596/install_flash_player_10_linux.deb) [/I]

---

### Post by walkerx on 2009-08-01
thanks all

---

### Post by Tclarkie on 2009-08-03
this works heaps well [http://ubuntuforums.org/showthread.php?t=1230177](http://ubuntuforums.org/showthread.php?t=1230177)

---

