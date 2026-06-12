---
title: "Emilia Pinball won't run"
date: 2010-12-24
forum: General Help
---

### Post by rapattack1 on 2010-12-24
Hi i installed Emilia pinball from the ubuntu software center and it won't open from the games menu. I don't know the command to open it from the terminal. I tried emilia and emiliapinball but nothing. I googled but every thread is 5 years or more older. Anyway got any suggestions? :0)

---

### Post by oldos2er on 2010-12-24
```
pinball
```

---

### Post by rapattack1 on 2010-12-24
I got this:
```
carla@carla-desktop:~$ pinball
Couldn't open config file: /home/carla/.emilia/pinball
Using default values
Initing SDL

0 joysticks were found.
Couldn't set video mode: Couldn't find matching GLX visual
carla@carla-desktop:~$ 


```
I used it on another install and didn't need a joystick

---

### Post by hhh on 2010-12-24
Is your video card capable of 3d acceleration? In a terminal, enter...
```
glxinfo | grep rendering
```
If it doesn't display "direct rendering: Yes" then you'll need to enable it, most likely by installing a restricted driver from System>Administration>Hardware Drivers.

---

### Post by rapattack1 on 2010-12-25
```
carla@carla-desktop:~$ glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
carla@carla-desktop:~$ 
```
OK I had a different video card in this machine and now. I had a nvidia card and can't remember what i have now. The nvidia was causing browser freezing. Now it is rare i get that . I am going to get a new agp card as soon as the shops open again.
So what i am saying is i installed the nvidia driver and now Hardware drivers is saying that 'no proprietry drivers are in use on this system'. This is after it does the search.
The Nvidia driver is installed and i got this when i click on the nvidia x settings:You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

Also did:
carla@carla-desktop:~$ sudo nvidia-xconfig

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by hhh on 2010-12-26
Sorry for the delay, holidays and all. I don't understand... you do NOT have an Nvidia card but you are trying to use an Nvidia driver? How is that supposed to work? Begin finding out what video card you have. See this page to start...
[https://help.ubuntu.com/community/RestrictedDrivers](https://help.ubuntu.com/community/RestrictedDrivers)

---

### Post by rapattack1 on 2010-12-26
Oh thats ok. Hope you had a great Xmas :0)
I had a nvidia card installed now i don't i think. Seems there is some problem in Ubuntu changing things. I don't know because i never changed a video card while using Ubuntu before. Is there a way to id the video card in Ubuntu? I don't know how to get rid of the nvidia driver and change things. Ok will read that page.

OK it says i have an ATI card!
carla@carla-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600]

OK that page seems to say that the ati driver is the default so if i uninstall the nvidia one in synaptic will it go back to the default?

---

### Post by hhh on 2010-12-27
Yes, it should, but you apparently still need to get 3d acceleration going. See this and/or post back here...
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by rapattack1 on 2010-12-27
Sorry I am not clear. Am i supposed to uninstall the nvidia driver first? There is a lot of that page...am i working from the 'Customized configuration for X.org, the new way' part of the page?

---

### Post by hhh on 2010-12-27
Uninstall the nVidia driver by running this in a terminal...
```
sudo apt-get purge nvidia*
```
Rename /etc/X11/xorg.conf to xorg.conf.bak

Reboot (have an Ubuntu Live CD ready in case everything goes haywire).

Is everything working? Try your pinball game again (there should be a launcher for it under Applications>Games). No go? Go to System>Administration>Hardware Drivers and install the recommended driver if there is one.

BTW, your going to kick yourself when you get this game running. It's meh.

---

### Post by rapattack1 on 2010-12-28
OK the command seemed to go well but i can find the exact file you named. There were back up files in the directory as you will see in the attached pic so i hope it will all work out. I have my livecd so will attempt a reboot now :0)

What is meh? I have used pinball before but it didn't require all this for it to run/install. Maybe it was simpler then?

---

### Post by rapattack1 on 2010-12-28
Yippee i got it running. Your a gem thanks so much! It is the same as i remember. Would be nice if someone put more into this game. I am from the era of the real pinball machines and we loved them. Not into all the shoot/kill stuff that is around now except galaga which i have installed also :0)

---

### Post by hhh on 2010-12-28
Glad you figured it out. Meh was my expression of low to medium enthusiasm for that game.

---

### Post by rapattack1 on 2010-12-28
:D
Ah now i know what that means thanks!
Yeah i was hoping the game progressed. Sadly no...ah well all is solved now :0)

---

