---
title: "How to install compiz on 11.10?"
date: 2011-10-26
forum: General Help
---

### Post by Nixarter on 2011-10-26
I've changed to gnome already.  I want compiz to work with it like it always has.  How do I do this?

I've searched the forums with different combinations, but it keeps coming back with no results found.

I tried installing compiz... only to find that it is already installed.  BUT, it is not in the program list.  Weird, I thought.  So I just tried running it.  It suggested "sudo compiz --replace"... so I did that, and it screwed up a lot of stuff, including killing the keyboard.  So I did a hard reset and it is back to the normal gnome, but still no compiz.

So, how do I get compiz installed and working on 11.10?

---

### Post by Nixarter on 2011-10-26
I now have conpizconfig settings manager installed.  But, no changed there are affecting the desktop.  For example, I set up the desktop cube and set opacity when not moving to 50%, but opacity is still 100%.  :(

---

### Post by xianbei on 2011-10-26
hit alt+f2 and type ccsm or compiz. Does nothing show?

then type:
```
sudo apt-get install compizconfig-settings-manager
```

voila?

---

### Post by Nixarter on 2011-10-26
I updated just before you posted that ;)

but I've done those things now, but to no avail.  The setting I change in ccsm doesn't actually affect anything.  This is really confusing.

---

### Post by stinkeye on 2011-10-26
Gnome-shell uses mutter as the window manager.
Compiz doesn't work with gnome-shell.

You need to login to an **Ubuntu** or **gnome classic** session to use compiz.

---

### Post by oldtimer7777 on 2011-10-26
> **stinkeye said:**
> Gnome-shell uses mutter as the window manager.
Compiz doesn't work with gnome-shell.

You need to login to an **Ubuntu** or **gnome classic** session to use compiz.

I can't get it to run either 11.10..  I would love to find out a way to get this to work.

In 10.10 all you had to do was click on Appearance, and then select Extra Effects, and the composition manager would automatically start.

I can't find that configuration window in 11.10.

---

### Post by stinkeye on 2011-10-26
Open the dash and start typing drivers and click on 
additional drivers and install and activate your gfx driver
and restart.

Also install **compizconfig-settings-manager** to check plugins are enabled.

---

### Post by Nixarter on 2011-10-27
dash?  where is that?

I found "additional drivers" and it only lists a wifi driver, and says there are no proprietary drivers installed.  So still no luck here.

I hope oldtimer7777 had better luck.

---

### Post by oldtimer7777 on 2011-10-27
> **Nixarter said:**
> dash?  where is that?

I found "additional drivers" and it only lists a wifi driver, and says there are no proprietary drivers installed.  So still no luck here.

I hope oldtimer7777 had better luck.

I'm sorry, I've been trying to use compiz since I installed 11.10, and it crashed my system. It is missing the configuration settings options in Appearance, like in 11.04. I'm going to wait until their is a easier way to set it up.

---

### Post by Nixarter on 2011-10-27
did you install "compizconfig-settings-manager"? I did, but it didn't help me.  If you haven't, just search ubuntu software center or synaptic (if you've installed it) for it.

---

### Post by oldtimer7777 on 2011-10-27
> **Nixarter said:**
> did you install "compizconfig-settings-manager"? I did, but it didn't help me.  If you haven't, just search ubuntu software center or synaptic (if you've installed it) for it.

I installed it. It wouldn't run after everything I tried. And then I started messing with it at the command line, and it was showing errors and just hanging there. No start on compositing.

---

### Post by stinkeye on 2011-10-27
If you can't install proprietary  drivers for your gfx card you won't be able to 
run compiz.

---

### Post by oldtimer7777 on 2011-10-27
> **stinkeye said:**
> If can't install proprietary  drivers for your gfx card you won't be able to 
run compiz.

I have never needed to install graphics drivers for my Toshiba laptop, and I have always used Compiz on previous releases of Ubuntu with no problem.  The option is missing in Appearance in 11.10.  There is no easy way to turn on 'Extra Effects" anymore.  It may not be a driver issue. Are you running Ubuntu 11.10?

---

### Post by stinkeye on 2011-10-27
Run this test command
```
/usr/lib/nux/unity_support_test -p
```

eg my output
```
glen@Oneiric:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 210/PCI/SSE2/3DNOW!
OpenGL version string:  3.3.0 NVIDIA 285.05.09

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
```

---

### Post by Nixarter on 2011-10-27
```
ubuntu@ubuntu:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 7.11

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

```

I am using gnome, though.  But I suppose that means it should support compiz as well?

---

### Post by stinkeye on 2011-10-27
The **gnome** session will not work with compiz.
Gnome-shell uses mutter as the window manager.

To have compiz as the window manager you need to log in to 
a **gnome-classic** or **Unity**  session.

So if you prefer gnome-shell you'll have to go without the compiz effects.

---

### Post by Nixarter on 2011-10-27
I restarted to log into gnome-classic... but found out that I have actually been in gnome classic this whole time, since I changed from unity.  So that's not the issue. :(

Any other ideas?

---

### Post by gandaran on 2011-10-27
> **Nixarter said:**
> I restarted to log into gnome-classic... but found out that I have actually been in gnome classic this whole time, since I changed from unity.  So that's not the issue. :(

Any other ideas?
does compiz really work on gnome 3?
or only works on the unity 3D desktop?

---

### Post by stinkeye on 2011-10-27
Okay I'll try and explain a few things.
I may make some mistakes so anyone who knows better feel free to correct me.

Gnome, gnome3, gnome-shell, gnome login session and gnome-classic 
can all be a little confusing.

Gnome is the desktop enviroment (kde is another)
Ubuntu 11.04 used gnome2(which is no longer being developed) 

gnome.org has moved on to developing and using gnome3
with the new gnome-shell using mutter as the window manager sitting on top.
Compiz will not work with gnome-shell. Gnome-shell is not included in the default 11.10 install.

Ubuntu 11.10 uses gnome3 with Unity which is a plugin for the Compiz window manager(included in default install) sitting on top.

To run Compiz you need:
* to install the proprietary drivers for you video card.(Look in system settings for **additional drivers**)
or
* have an nvidia card which is compatible with the included open source nouveau drivers.



_Explanation of session choices at the lightdm greeter_
# **GNOME Classic**-  a version of the old panels for running compiz as the window manager (if desired) with the unity plugin disabled
# **Gnome Classic(No effects)**- for running Metacity as the window manager
# **Ubuntu **- session running Compiz with the Unity plugin enabled
# **Ubuntu 2d**- session running a tweaked version of Metacity for unity2d for unsupported or older video cards.

      and if you install gnome-shell you will have
# **GNOME**- a session running gnome-shell which uses Mutter as the window manager...(compiz doesn't work with gnome-shell)


_Some Tips_
To find the video driver in use run
```
lspci -k | grep -A3 VGA
or
lsmod | grep video
```


To test the capability of your video card run...
```
/usr/lib/nux/unity_support_test -p
```


To find what window manager you are using(needs installation of **wmctrl**)
```
wmctrl -m | grep Name
```


To show the session you are logged in to
```
echo $DESKTOP_SESSION
```

When playing around with compiz it's handy to have an alternative way
of opening a terminal or running a command as sometimes keyboard shortcuts don't work and you have no menus.
Quite often compiz will not load properly after changing a setting in ccsm
but usually can be fixed by running 
```
compiz --replace
```

I find the best backup is to install **easystroke** (mouse gestures)
and set gestures for the commands...
compiz --replace
and
gnome-terminal

---

### Post by stewi1014 on 2011-11-05
this is really annoying, I tried "compiz --replace", and the everything went screwball, the dock disappeared, so did the title bar on all the windows and i had to restart! and now if i try to boot into Unity, there is no dock, i have to use Unity 2d. i think compiz and compizconfig should come standard with ubuntu and should ACTUALLY WORK (*hint there to the Dev's of whatever has broken it)

---

### Post by stinkeye on 2011-11-05
While in your 2d session install compiconfig-settings-manager.

In the dash run ccsm and go to preferences and click on the defaults button.
Then hit the back button and enable the unity plugin under Desktop.

The panel and launcher should now be back next time you log in to the ubuntu session.

Sometimes the compiz --replace command can take 30 secs or more to run 
and even then has to be run again.
If that doesn't work then do as I described earlier and set to defaults and re-enable unity in your 2d session.

---

### Post by linuxaddix on 2011-11-05
[http://ubuntuforums.org/showthread.php?t=1864603](http://ubuntuforums.org/showthread.php?t=1864603)
in my post you will find how to use compiz in 11.10

---

### Post by linuxaddix on 2011-11-05
btw you dont have to be in 2d to install the compiz you can do it from the desktop setting "Ubuntu"
hope it helps and just a fore warning you might get a lot of twitches while enabling things in compiz but not to worry its just making its settings.just follow as ive posted and you should be fine

---

### Post by stinkeye on 2011-11-05
> **linuxaddix said:**
> btw you dont have to be in 2d to install the compiz you can do it from the desktop setting "Ubuntu"
hope it helps and just a fore warning you might get a lot of twitches while enabling things in compiz but not to worry its just making its settings.just follow as ive posted and you should be fine
You can but for some people it's easier to do it from the 2d session
where you don't need to use the terminal and occasionally you don't
have the ctrl+alt+t terminal shortcut.

P.S. I just posted in one of your threads showing how to get fusion-icon in the panel.

---

### Post by linuxaddix on 2011-11-06
thanks stink eye i forgot to post solved the day after i posted it.

---

