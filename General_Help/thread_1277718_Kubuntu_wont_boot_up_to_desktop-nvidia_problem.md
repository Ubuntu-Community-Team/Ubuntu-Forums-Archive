---
title: "Kubuntu wont boot up to desktop-nvidia problem"
date: 2009-09-28
forum: General Help
---

### Post by xxterry1xx on 2009-09-28
Hello i was updateing kubuntu by some commands like apt-get update and some other commands and i installed all blocked updates and other updates and i seen a nvidia driver so i installed and now i boot up it says low res screen mode and then it gives me options to troubleshoot and that i tryed installing the nvidia driver again by tty1 but it wouldnt work any ideas? please help.

---

### Post by TombKing on 2009-09-28
see [http://ubuntuforums.org/showthread.php?t=1276547](http://ubuntuforums.org/showthread.php?t=1276547)

I had a black screen after booting with the 180 version of the driver.

Not sure of the restart command for KDE but as in that thread I got a usable desktop back, removed the 180 version of the driver and tried version 96 and it works.

---

### Post by xxterry1xx on 2009-09-28
> **TombKing said:**
> see [http://ubuntuforums.org/showthread.php?t=1276547](http://ubuntuforums.org/showthread.php?t=1276547)

I had a black screen after booting with the 180 version of the driver.

Not sure of the restart command for KDE but as in that thread I got a usable desktop back, removed the 180 version of the driver and tried version 96 and it works. thanks for the post i went to recovery mode and i fixed a couple of stuff like the graphics driver now im getting this message when i install the 190 driver(latest beta)

 SystemError: E:Unable to correct problems, you have held broken packages.

i tryed apt-get install -f
but it didnt work 
o also can you please give me the 185 apt-get link? i have the nvidia in my sources list

edit
i got the drivers from here [http://www.ubuntugeek.com/howto-install-nvidia-190-25-beta-drivers-in-ubuntu-jauntyintrepidhardy.html](http://www.ubuntugeek.com/howto-install-nvidia-190-25-beta-drivers-in-ubuntu-jauntyintrepidhardy.html)
i tryed those again and it didnt work it said 

root@terry-linksoftware:~# sudo apt-get install nvidia-190-modaliases nvidia-glx-190
Reading package lists... Done
Building dependency tree
Reading state information... Done
nvidia-190-modaliases is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  nvidia-glx-190: Depends: nvidia-190-libvdpau (>= 190.32) but it is not going to be installed
E: Broken packages

and im useing kubuntu 9.04 jaunty

---

### Post by xxterry1xx on 2009-09-28
bump

---

### Post by TombKing on 2009-09-29
Note I said I used version 96 the older version and it worked for me.

---

### Post by ibuclaw on 2009-09-29
If you want to use the 190 beta drivers, I prefer manually compiling: [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

Each to his own though.

Regards
Iain

---

### Post by xxterry1xx on 2009-09-29
> **tinivole said:**
> If you want to use the 190 beta drivers, I prefer manually compiling: [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

Each to his own though.

Regards
Iain
nvm i did it another way it worked im useing the 185 right now and thanks

---

