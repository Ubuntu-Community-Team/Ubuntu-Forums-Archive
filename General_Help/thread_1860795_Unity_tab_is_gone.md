---
title: "Unity tab is gone"
date: 2011-10-15
forum: General Help
---

### Post by Diary on 2011-10-15
I have installed Ubuntu 11.10 and then intalled the CompizConfig Settings Manager after that unity tab and shutdown and system tray is gone 

> DISPLAY=:0.0 /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7050 / nForce 610i/PCI/SSE2
OpenGL version string:  2.1.2 NVIDIA 280.13

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes


---

### Post by soulheart17 on 2011-10-15
yeah i am also suffering from same problem i got screen like this

---

### Post by sikander3786 on 2011-10-15
> **Diary said:**
> I have installed Ubuntu 11.10 and then intalled the CompizConfig Settings Manager after that unity tab and shutdown and system tray is gone
Press Alt + Ctrl + F2 at the desktop and login to console using your credentials. Run:

```
DISPLAY=:0.0 ccsm
```

Make sure 'Desktop Wall' and 'Ubuntu Unity Plugin' are enabled. Also take a look at this troubleshooting guide:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by dino99 on 2011-10-15
unity --reset

---

### Post by garvinrick4 on 2011-10-15
ctrl/alt/t
and in the terminal that opens
```
unity --reset
```

---

### Post by sikander3786 on 2011-10-15
> **soulheart17 said:**
> yeah i am also suffering from same problem i got screen like this
You are running the Gnome Fallback Session somehow. It doesn't come installed by default so you must have installed it yourself by either directly installing it or by indirectly installing it alongwith Gnome Shell.

If LightDM isn't set to autologin, you can simply hard reset your PC and then choose 'Ubuntu' in the sessions option by clicking the small wheel button besides your username.

If LightDM is set to autologin, press Alt + Ctrl + F2 and follow the "Configuration File Method" here to revert your session to Unity.

[http://www.tuxgarage.com/2011/09/setting-lightdm-to-auto-login-oneiric.html](http://www.tuxgarage.com/2011/09/setting-lightdm-to-auto-login-oneiric.html)

---

### Post by Diary on 2011-10-15
> **sikander3786 said:**
> Press Alt + Ctrl + F2 at the desktop and login to console using your credentials. Run:

```
DISPLAY=:0.0 ccsm
```Make sure 'Desktop Wall' and 'Ubuntu Unity Plugin' are enabled. Also take a look at this troubleshooting guide:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

> **dino99 said:**
> unity --reset

tried those command not working

---

### Post by soulheart17 on 2011-10-15
thx unity --reset solve my problem

---

### Post by JazzPotato on 2011-10-15
Hi I had the same problem, if you go into compiz config settings if you have it installed, find ubuntu unity plugin and click the checkbox that says enable ubuntu unity plugin. I have experienced several other bugs like windows behaving strangely, etc... Oneiric is still young so Im sure theese will get fixed.
Thx

---

### Post by garvinrick4 on 2011-10-15
> tried those command not working```
sudo apt-get install compizconfig-settings-manager
```Go into dash and type compiz will pop up first open.
And then make sure unity plugin and Desktop wall are checked as in previous post 6's link.

---

### Post by Diary on 2011-10-15
> **garvinrick4 said:**
> ```
sudo apt-get install compizconfig-settings-manager
```Go into dash and type compiz will pop up first open.
And then make sure unity plugin and Desktop wall are checked as in previous post 6's link.

thanks dude for the tip

I have checked the Ubuntu Unity Plugin, now working fine :)

---

### Post by David006 on 2011-10-15
> **sikander3786 said:**
> Press Alt + Ctrl + F2 at the desktop and login to console using your credentials. Run:

```
DISPLAY=:0.0 ccsm
```

Make sure 'Desktop Wall' and 'Ubuntu Unity Plugin' are enabled. Also take a look at this troubleshooting guide:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

This worked for me.  And, I had already unsuccessfully tried ALL other methods found (including: service lightdm stop/start; gconftool-2 ..; unity --reset; etc.).

Note: Ubuntu 11.10 and Unity (3D) was initially working Ok, after upgrade from Ubuntu 11.04 ..


Background: I upgraded (when prompted) from Ubuntu 11.04 to 11.10 ..  Previously I had 'Unity' disabled (ie. 'Classic Mode' at login) under 11.04 .  I (wisely?) changed back to Unity, before starting, but did not remove (Ubuntu Tweak) desktop icons.

When I attempted to tidy-up (see list), I lost the button-bar (left-hand margin) AND the ability to logout, etc.
 - tried to remove: Appmenu (Global Menu)  [inconsistent]
 - tried to remove: 'trash', 'home' icons (installed by UTweak)  [failed, every time]
 - tried to 'identify' stability issues, with Workspace switcher / Alt-Tab ..  [inconsistent]


Note: I was able to re-start using Ctrl-Alt-F2, (login), 'sudo shutdown -r now' ..


THIS IS STILL NOT STABLE ENOUGH TO USE.

( Sticking with 2D for now. )

---

### Post by garvinrick4 on 2011-10-15
> Note: Ubuntu 11.10 and Unity (3D) was initially working Ok, after upgrade from Ubuntu 11.04 ..I am happy you told users that it was your attempts to alter install that made your system
as you say to unstable to use.

To remove or add the home and trash icons. (If do not have app configuration editor install
in ubuntu software center.)
Configuration editor to app to nautilus to desktop, remove tick mark in boxes and close, click on screenshot.

---

### Post by WB0HYQ on 2011-10-16
None of the commands given in this thread have brought back my unity desktop.  That includes the links given to other threads.  Most of the commands will spout lots of ERROR lines telling em that some things are 'already defined', then several more commands execute.  Following that (which takes place in about 15 seconds) the command window simply stops.  No prompt - no nothing.  I've waited as long as 10 minutes, then hit Crtl-C. This seems to upset something because I get a few lines of status reports, then the cursor stops.  Again, no prompt.

Does this mean I have to completely re-install the OS?  I really hate to do that because I've personalized it quite a bit and installed about 20 packages.

Bill

---

### Post by Al from JerZ on 2011-10-27
same here. I tried everything and still my side bar is missing. :confused:
This is the last thing I did prior to this fiasco:
Installed compiz, messed around with settings for the first time and attempted to do the cube desktop thing. When doing so it prompted me to disable unity and i think thats where it all went wrong. 
Its not a big deal if i have to reinstall as i havent done much yet but I really would like to learn how to fix this issue for future reference. 
I wish I could revert to my settings before messing with compiz.....this is going to make me hessitant to mess with compiz in the future for sure.
 
FYI:
Im running closed source ATI drivers (sucessfully). Im running dual monitors, mirrored (hdmi to my tv and dvi to my 17 dell screen)
Im a total newb at linux, only been messing with it for 2 days

---

### Post by garvinrick4 on 2011-10-27
Look at mc4man's posts in this thread for compiz problems.
[http://ubuntuforums.org/showthread.php?t=1869335](http://ubuntuforums.org/showthread.php?t=1869335)

---

### Post by Al from JerZ on 2011-10-27
> **garvinrick4 said:**
> Look at mc4man's posts in this thread for compiz problems.
[http://ubuntuforums.org/showthread.php?t=1869335](http://ubuntuforums.org/showthread.php?t=1869335)

when i enter the nautilus code mc4man provides (im entering exactly as he posted, not sure if i should be omiting any of the code he posts)  it says:
Could not parse  argument: Cannot open display:

when i enter ccsm jt post about 12 lines of code last one being an error:
AttributeError: 'NoneType' object has no attribute 'get_default_screen'

Not sure if any of that can shed light on my issue but im grateful for any suggestions.

---

### Post by Al from JerZ on 2011-10-27
UPDATE!!
my side bar is back!  Thanks for leading me in the right direction.  what i ended up doing was **installing Gnome Classic and runining the nautilus code recommended earlier**, the code worked in gnome classic.  I then logged into Ubuntu and all was well (or so it seems).

---

### Post by garvinrick4 on 2011-10-27
> UPDATE!!
my side bar is back!  Thanks for leading me in the right direction. 
No problem,
You can usually take a mc4man post to the bank.

---

