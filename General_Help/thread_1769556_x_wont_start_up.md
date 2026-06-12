---
title: "x wont start up"
date: 2011-05-28
forum: General Help
---

### Post by freeburn on 2011-05-28
after i upgraded to natty unity was very sloppy and frequently crashed. so i switched to kde. now i always update using my local mirror. but after 20 days without any update i suspected that my local mirror is not in sync with master mirror. because i saw numarous updates were listed in ubuntuupdates.org. so i switched to the master mirror and found about 2 gigs of update is pending. so it may be the case that when i updated to natty i wasnt in sync with all the packages because of the local mirror disfunction. however as i started upgrading at little chunks as i do not get a lot of speed when i update using master mirror. it was going well. yesterday i updated my development stuff like gcc, llvm, haskell etc. next i update kde stuffz. next i updated glibc. after upgrading glibc upon reboot it stuck after showing splash. it prints a msg like System V runlevel. nothing shows up. i switched to virtual console and saw xserver is probably running. i started gdm/kdm from console but it does not recognize my mouse or keyboard. so i have no option other then logging in from my laptop using ssh. if i run recovery console and try to run failsafe login it complains that my monitor ,mouse and keyboard is not configured. then first i reconfigured xorg. with no luck i then updated all xserver related packages. again with no luck. i try to find something in kdm log , gdm log and xorg log. the exact things i cant paste here right now because i'm typing from office. but kdm log reports about a memory leak(double free). xorg log reports a (EE) saying frame buffer (fbcon) is in trouble. my gdm log(i tried this with both gdm and kdm) also posts some (EE) which i do not remember right now. i will update it later. 

my video card is intel, i have tried erlier kernel version without any luck, no broken packages are listed

thats all i guess. please help me, this worksation is like a girlfriend to me because i went through lot of pain to set up all the development environments.

thanks in advance

---

### Post by LowSky on 2011-05-28
I would try finishing your updates from terminal

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by freeburn on 2011-05-28
full update is going on now, it was running for all the night :) 

and the funny part is our government is thinking of exporting unused bandwidth :)

sorry for the off topic, but i could not resist :)

---

