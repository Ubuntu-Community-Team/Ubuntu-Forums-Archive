---
title: "Ubuntu GUI doesn't load at boot"
date: 2009-08-21
forum: General Help
---

### Post by sevansbr on 2009-08-21
Hello out there,

I'm pretty new to this, so forgive if my terminology is off, or if I'm not giving enough information. 

I'm running a Hardy (8.04) and I've been trying to get a microphone to work. In the process of doing so I reinstalled my ALSA drivers, following the instructions from this post because I managed to break my sound in the process: [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+solution](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+solution).

After having run:
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```
and then:
```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

I rebooted, and when I did, the GUI didn't load! I was asked to enter my username and password into what looked like an MS-DOS type prompt, and then was given just a command prompt after having done so. After some research I discovered that I could load the Ubuntu GUI by typing startX. However, shutting down is now a pain because the shut-down button does not have a shut-down option anymore, just log-out and hibernate.

So, I'm utterly stumped. Any hints?

---

### Post by fooman on 2009-08-21
log out and when you get to the console screen (no gui)...type:

```
sudo reboot
```

when it reboots,  look for the grub menu and choose recovery mode.  when the recovery mode menu appears...try the xfix option,  then continue with normal boot.

see if that gets you back to the desktop.  if it does,  you may have to reinstall your graphics driver once there.

hope that helps.

---

### Post by sevansbr on 2009-08-21
Thanks for the response fooman.

I gave that a try, but no dice. Still have to log in the console and start the GUI with startx. What exactly did I just do?

---

### Post by fooman on 2009-08-21
just checked that page you linked to....did you see this "very important" part?
> 
[SIZE=2]**VERY IMPORTANT NOTE: **Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following[/SIZE]
[SIZE=2] 	Code:
 	sudo apt-get install gdm ubuntu-desktop 
 [/SIZE]

try running that command:

```
sudo apt-get install gdm ubuntu-desktop
```

then reboot.

hopefully,  that will set you straight.

---

### Post by sevansbr on 2009-08-21
hahaha, indeed I did, but didn't really know what that meant...

Appreciate your help, fooman. Even if I could have helped myself but just not being a knucklehead. 

Cheers, and I hope this helps other knuckleheads

---

