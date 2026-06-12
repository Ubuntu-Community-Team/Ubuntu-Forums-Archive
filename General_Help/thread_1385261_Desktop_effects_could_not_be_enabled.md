---
title: "Desktop effects could not be enabled"
date: 2010-01-19
forum: General Help
---

### Post by llawwehttam on 2010-01-19
I have been using ubuntu for a long time with no problems. I used the destop effects with 8.10, 9.04 and now with 9.10 and It worked fine. A while ago however they just stopped working one day and I go the error > Desktop effects could not be enabled when I tried to enable them.

To fix this I set a script to run at startup with ```
compiz --replace
```in it and that worked fine until now.

Today my desktop effects went again.

Here are some possible useful outputs:

```
llawwehttam@Deadlock:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

 
``````
llawwehttam@Deadlock:~$ glxinfo | grep "direct rendering"
direct rendering: Yes

``````
llawwehttam@Deadlock:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] [1002:5159]

``````
llawwehttam@Deadlock:~$ glxinfo | grep vendorserver glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project

``````
llawwehttam@Deadlock:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 


```any ideas appreciated.

---

### Post by llawwehttam on 2010-01-21
```
sudo bump
```

This is really starting to get annoying but I am seriously considering getting a new graphics card so if it can't be fixed I'm not too bothered.
I have had a lot more problems with Karmic than I ever had with Jaunty though.

---

### Post by spoon_ on 2010-01-22
Hey, my desktop effects mysteriously died today too!

> 
spoon@table:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 


---

### Post by spoon_ on 2010-01-22
Oh, reinstalling Nvidia driver fixed it.

---

### Post by timgood on 2010-01-22
I've just had to do this as well. Something in recent updates?

---

### Post by Saiko Berry on 2010-01-22
Linux runs fine without desktop effects. Nothing of value was lost.

---

### Post by timgood on 2010-01-23
> **Saiko Berry said:**
> Linux runs fine without desktop effects. Nothing of value was lost.

Don't think that's the point. If something is broken, it's broken. You may not be bothered by it, but others are.

---

### Post by llawwehttam on 2010-01-23
What's starting to really annoy me is that avant window manager does rely on a compozitioning manager so its not the desktop effects I need to work, its just compiz as I used to have a dock and no panels, its a bit annoying not having them.
( i did have a backup of my panel so I'm not too worried)

---

### Post by llawwehttam on 2010-01-23
I've just done a bit of fiddling and I have managed to get it working again for me. 

> **timgood said:**
> I've just had to do this as well. Something in recent updates?

I think the update they released lets compiz work without a startup entry. ( possibly)
If your nvidia drivers have stopped working then it was a kernel update that did it and you should use this:

[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

READ THIS BEFORE DOING ANYTHING AND READ IT PROPERLY!

If you are running nvidia-drivers then re-install them and the problem should be fixed.
If you are running mesa or opensource radeon drivers then read on.

 right , just to clarify REMOVE any script you have running, that means REMOVE ( not type in terminal) ```
compiz --replace
``` from the  startup programs as it will cause problems. Once you have changed the setting in your gnome configuration 
```
Apps/ metacity/ general/ compositioning_manager
``` to true  then you should be able to re-enable effects. After that they worked on login for me without a script.

Hope that helps people.

( as this fix worked for me I will mark It as solved. If your similar problem persists then start a new thread)

---

### Post by llawwehttam on 2010-02-05
After updating to day the problem has come back and 
```
compiz --replace
```
or the above method no longer work.

---

### Post by llawwehttam on 2010-02-05
Just tried compiz icon but when I reload compiz with it all I get is a white screen.
Any ideas.

---

### Post by The Funkbomb on 2010-02-05
I'm having the same issue.  Some update today blew out my system :(

---

### Post by llawwehttam on 2010-02-05
I get this from compiz-check-->
```
llawwehttam@Deadlock:~/Desktop$ sh compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 


```

---

### Post by llawwehttam on 2010-02-05
Well until I can fix this I will be using openbox as my window manager. Compiz is fine on my laptop with nvidia card but this seems to be caused by either a confilict between the new kernel and mesa or something similar.

---

### Post by llawwehttam on 2010-02-05
I have managed to fix it again. After enableing the xorg ppa and updating, installing openbox, installing compiz-fusion-icon and setting it to use openbox, then rebooting and enabling desktop effects it worked.
If I let it search for drivers then it fails but if I press cancel before It can it enables them and works. I don't know why but it works.

---

