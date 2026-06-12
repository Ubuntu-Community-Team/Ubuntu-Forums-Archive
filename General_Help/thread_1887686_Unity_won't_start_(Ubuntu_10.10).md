---
title: "Unity won't start (Ubuntu 10.10)"
date: 2011-11-27
forum: General Help
---

### Post by asuastrophysics on 2011-11-27
Hey guys,

I'm having a small problem where I can't get unity to start. I installed unity by running ```
sudo apt-get install unity
``` in the terminal. 

Then I logged out of my account, and logged back in, making sure to select unity at the login screen. When I log in, nothing appears. I don't have the menu on the left or on the top. It also appears that the windowing manager isn't started, as I have no desktop icons. 

My graphics card is an nVidia 8600. Any ideas?

---

### Post by oldtimer7777 on 2011-11-27
In terminal try:

sudo apt-get install ubuntu-desktop

> **asuastrophysics said:**
> Hey guys,

I'm having a small problem where I can't get unity to start. I installed unity by running ```
sudo apt-get install unity
``` in the terminal. 

Then I logged out of my account, and logged back in, making sure to select unity at the login screen. When I log in, nothing appears. I don't have the menu on the left or on the top. It also appears that the windowing manager isn't started, as I have no desktop icons. 

My graphics card is an nVidia 8600. Any ideas?

---

### Post by asuastrophysics on 2011-11-27
> **oldtimer7777 said:**
> In terminal try:

sudo apt-get install ubuntu-desktop

Thanks for your response! But it appears it's already installed.
```
jakob@jake-desktop:~$ sudo apt-get install ubuntu-desktop
[sudo] password for jakob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jakob@jake-desktop:~$ 

```

If I try to launch unity from terminal, I get this:
```
jakob@jake-desktop:~$ unity

Clutk-ERROR **: Unable to initialise Glew: glewInit Error: Missing GL version
aborting...
Aborted
jakob@jake-desktop:~$ 

```

weird. What do you think is wrong?

---

### Post by oldtimer7777 on 2011-11-27
I would suggest uninstalling compiz display manager.

> **asuastrophysics said:**
> Thanks for your response! But it appears it's already installed.
```
jakob@jake-desktop:~$ sudo apt-get install ubuntu-desktop
[sudo] password for jakob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jakob@jake-desktop:~$ 

```If I try to launch unity from terminal, I get this:
```
jakob@jake-desktop:~$ unity

Clutk-ERROR **: Unable to initialise Glew: glewInit Error: Missing GL version
aborting...
Aborted
jakob@jake-desktop:~$ 

```weird. What do you think is wrong?

---

### Post by asuastrophysics on 2011-11-27
It appears that unity is not starting because Compiz won't start. If I try to launch compiz, this is what I get: 
```
jakob@jake-desktop:~$ compiz
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: glXCreateContext failed
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

```

Does anyone know how to fix this? I'm pretty sure that if I can get compiz to start, I can get unity to start successfully.

---

### Post by oldtimer7777 on 2011-11-27
Yes, the solution is to uninstall compiz for now.

You can reinstall it when you have your graphic driver updated.

> **asuastrophysics said:**
> It appears that unity is not starting because Compiz won't start. If I try to launch compiz, this is what I get: 
```
jakob@jake-desktop:~$ compiz
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: glXCreateContext failed
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

```Does anyone know how to fix this? I'm pretty sure that if I can get compiz to start, I can get unity to start successfully.

---

