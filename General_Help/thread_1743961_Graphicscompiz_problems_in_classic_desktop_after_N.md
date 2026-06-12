---
title: "Graphics/compiz problems in classic desktop after Natty upgrade"
date: 2011-04-29
forum: General Help
---

### Post by hitchhiker4242 on 2011-04-29
Earlier today I upgraded to Natty and have been using the classic desktop. Everything was going fine until about half an hour ago I suddenly started having problems. I wasn't really doing anything, just web browsing when this started. Every few minutes my desktop will freak out. Docky freezes and gets this big black rectangle around it, my windows and gnome panel disappear, then a few seconds later it all comes back only it isn't working properly. For example if I mouse over my home folder on Docky, the zoom effect will be a few icons above my cursor, and if I click it will launch an application a few icons above my cursor as well. Random compiz effects stop working, like the shiver effect on menus, and if I click on something in the gnome panel everything freaks out again. If I walk away for maybe ten minutes and come back suddenly everything is working properly again. But after a minute or two the same thing repeats itself. Any ideas? I would greatly appreciate it.

---

### Post by immy123 on 2011-04-29
I have the same problem too. Are you using intel VGA graphics?

Anyway, the problem seems to be with compiz and/or possibly with the xserver-xorg-video-intel package driver. This has mostly affected graphics with GPUs, but mine is legacy VGA. Sadly I still haven't seen a proper fix for this so far, yet alone an update. :(

As for a temporary fix, try disabling docky and use metacity instead of compiz. If you find it difficult to do this after logging into your desktop, then try logging out or reboot and get to the login screen. Choose your username or type it, and then you'll see which session to choose in the bottom panel. Choose the gnome classic desktop with no effects option. After logging into the desktop things should be much better than before, though there will still be a little graphic corruption and flashing once in a while.

---

### Post by hitchhiker4242 on 2011-04-30
I have an Asus UL30a, can't remember the exact specs. I'm pretty sure it has Intel GMA. What sucks the most about it is that it was working fine for hours before this happened. Honestly I'd rather go back to 10.10 for a while than have to not use things I want to use. I hope somebody can figure this out.

---

### Post by immy123 on 2011-04-30
Well, I just tried pressing ALT+F2 and ran gnome-panel --replace. The graphic corruption has gone and so are the rendering issues in chrome. Seems to be another temporary fix. Let me know what happens after trying this out. :D

---

### Post by shahraeini on 2011-04-30
I had the same problem, this was the reason I hate natty and Unity!!! in ubuntu 10.10 I had tried notebook edition and after 2 days I found out unity was awful as hell!!! today I completely purge compiz and install it again, till now it's work, but I'm not sure it will be...
> **hitchhiker4242 said:**
> Earlier today I upgraded to Natty and have been using the classic desktop. Everything was going fine until about half an hour ago I suddenly started having problems. I wasn't really doing anything, just web browsing when this started. Every few minutes my desktop will freak out. Docky freezes and gets this big black rectangle around it, my windows and gnome panel disappear, then a few seconds later it all comes back only it isn't working properly. For example if I mouse over my home folder on Docky, the zoom effect will be a few icons above my cursor, and if I click it will launch an application a few icons above my cursor as well. Random compiz effects stop working, like the shiver effect on menus, and if I click on something in the gnome panel everything freaks out again. If I walk away for maybe ten minutes and come back suddenly everything is working properly again. But after a minute or two the same thing repeats itself. Any ideas? I would greatly appreciate it.

---

### Post by hitchhiker4242 on 2011-04-30
@immy123: This didn't make a difference for me unfortunately. 

@shahraeini: I know right? I've been using Unity since yesterday since it's the only thing that is working for me right now. It's ok, but its just plain not as functional and not very configurable. How do you purge and reinstall compiz?

---

### Post by immy123 on 2011-04-30
> @shahraeini: I know right? I've been using Unity since yesterday since it's the only thing that is working for me right now. It's ok, but its just plain not as functional and not very configurable. How do you purge and reinstall compiz?

Press ALT+F2 and enter gksu synaptic and then enter your password when prompted. After synaptic opens up, enter compiz in the search bar. Right click on compiz and 'Mark for complete removal'. Click apply and compiz should be purged. To reinstall, just right click on compiz again and 'Mark for installation' and click apply. Hope this will work for you.

Btw, there's a bug already reported on this issue -
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/762135](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/762135)

You might find something useful there.

---

### Post by shahraeini on 2011-04-30
> **immy123 said:**
> Press ALT+F2 and enter gksu synaptic and then enter your password when prompted. After synaptic opens up, enter compiz in the search bar. Right click on compiz and 'Mark for complete removal'. Click apply and compiz should be purged. To reinstall, just right click on compiz again and 'Mark for installation' and click apply. Hope this will work for you.

Btw, there's a bug already reported on this issue -
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/762135](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/762135)

You might find something useful there.
thanks for your quick reply, I did your suggestion but unfortunately as I expect it didn't work... you know there are 2 different compizS available on natty software center, first one has a name "compiz" and a description like this: "OpenGL window and compositing manager" and the second one is inverse has a name: "OpenGL window and compositing manager" and a description "compiz". the second one makes a trouble for my laptop ...

---

### Post by rtimai on 2011-05-01
I experienced "fatal" graphics corruption with Unity also. I don't remember what I was doing when the screen suddenly displayed the contents of several windows mixed together with no window borders, then the icons along the left screen edge all disappeared, the top panel displayed corrupted text, and nothing responded to mouse clicks or right-clicks. There was no graphical way to shut down except by going to Ctl-Alt-F1 Terminal and entering "sudo shutdown now". Restarting displayed only the wallpaper and a few icons to documents that I had put there for quick access (documents that I was reading through.) Oddly enough, they worked, opening the documents. 

THANK GOODNESS for the Ubuntu Classic Desktop option on login. I didn't realize that the alternate desktop options only appeared after selecting a user, and I restarted a half-dozen times before I finally saw it.

My graphics system:

ATI Technologies Inc M880G [Mobility Radeon HD 4200]
(HP dv6 3012he notebook)


I have checked System > Administration > Additional Drivers, and found the following available:
------
ATI/AMD proprietary FGLRX graphics driver
3D-accelerated proprietary graphics driver for ATI cards.

This driver is required to fully utilise the 3D potential of some ATI graphics cards, as well as provide 2D acceleration of newer cards.
------

I activated (installed) this driver after switching to Metacity (the Classic Gnome 2 desktop,) as I couldn't resist the driver description.) However, I have not found the courage to re-try Unity/Compiz.

I have never been much for eye-candy anyway. I didn't find Unity so very convenient as some have raved on about. I think I prefer the classic desktop where I can see my active windows in a bottom status panel. Unity hides too many processes and available tools.

shahraeini:
> there are 2 different compizS available on natty software center, first one has a 
> name "compiz" and a description like this: "OpenGL window and compositing manager" 
> and the second one is inverse has a name: "OpenGL window and compositing manager" 
> and a description "compiz". the second one makes a trouble for my laptop ...

The two compizs you mentioned are the same thing, one is a meta-package (kind of like an alias that always references the most current version.) There are however, additional packages, a Simple Compiz-Config, and Advanced Compiz-Config. Not that we'd want to install them until Unity is fixed for greater compatibility.

I just remembered, when I rebooted while holding the SHIFT key to display the bootup options, and I selected Recovery Mode, a window popped up warning me that my hardware was not compatible with advanced graphic features, and that I should select Classic Ubuntu when logging in. I don't remember the exact wording, but it was something like that. So somewhere, the system is aware that my graphics system is not supported in Unity.

---

### Post by shahraeini on 2011-05-01
I think our problem related to compiz. I hope someone find a solution for compiz compatibility with natty ubuntu classic!

---

### Post by hitchhiker4242 on 2011-05-01
I have also noticed that there seem to be different compiz's floating around. Apparently though, this problem goes beyond just compiz, at least in my case. Even after I had completely removed as per the instructions above, I was still experiencing some weird hiccups and whenever I touch the panel things start crashing. I know my hardware can handle it because Unity works just fine. Only the classic desktop is totally broken. :-({|=

---

### Post by shahraeini on 2011-05-01
I've solved it by

sudo apt-get remove compiz compiz-core compiz-dev compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-kde emerald --purge

then

metacity --replace


> **hitchhiker4242 said:**
> I have also noticed that there seem to be different compiz's floating around. Apparently though, this problem goes beyond just compiz, at least in my case. Even after I had completely removed as per the instructions above, I was still experiencing some weird hiccups and whenever I touch the panel things start crashing. I know my hardware can handle it because Unity works just fine. Only the classic desktop is totally broken. :-({|=

---

### Post by filster on 2011-05-01
> **hitchhiker4242 said:**
> Earlier today I upgraded to Natty and have been using the classic desktop. Everything was going fine until about half an hour ago I suddenly started having problems. I wasn't really doing anything, just web browsing when this started. Every few minutes my desktop will freak out. Docky freezes and gets this big black rectangle around it, my windows and gnome panel disappear, then a few seconds later it all comes back only it isn't working properly. For example if I mouse over my home folder on Docky, the zoom effect will be a few icons above my cursor, and if I click it will launch an application a few icons above my cursor as well. Random compiz effects stop working, like the shiver effect on menus, and if I click on something in the gnome panel everything freaks out again. If I walk away for maybe ten minutes and come back suddenly everything is working properly again. But after a minute or two the same thing repeats itself. Any ideas? I would greatly appreciate it.

Guys, it is most probably a driver problem, not a compiz problem itself. Proprietary drivers don't work, you don't have 3D support and of course compiz and fancy docks don't work (since they require additional graphic support). Many people have this problem and many think that it's a buggy compiz/unity, but it's not. Check your additional drivers and if you see "active but not in use", welcome aboard.

---

### Post by rtimai on 2011-05-01
filster,

For the record I installed the ATI/AMD proprietary FGLRX graphics driver for the ATI M880G [Mobility Radeon HD 4200 and had usability issues with the OEM driver, e.g., pull-down menus were obscured by the main window content and totally unusable. I reverted to the open source driver and the problems went away. In other words, I never got a chance to try Unity with the ATI/AMD driver.

---

### Post by afrodeity on 2011-05-02
This works for the Unity desktop

```

gconftool --recursive-unset /apps/compiz-1
gconftool --recursive-unset /apps/compizconfig-1

```

Still no fix for the Classic desktop. Only thing that works is metacity.

see my[ thread ]("http://ubuntuforums.org/showthread.php?t=1745765")

---

### Post by ben2talk on 2011-05-03
Well the initial upgrade failed to boot to desktop - until I got to the recovery options and booted failsafe and installed the nVidia driver again - however, compiz is NOT running quite as it did before.

I had issues whereby every time I clicked a window it was pushed to the back, also failure of compoziting (big black squares appearing, decorations corrupting etc).

The most noticeable difference for me is that 'Simple Compiz Config' is broken now, and even though I set in gconf-settings and in compiz that double clicking titlebars should toggle_maximize_vertical - they insist on simply maximising unless I replace compiz with metacity.

I sure wish that Canonical would come up with a new and improved composite manager - there's nothing to compare with gnome and compiz in terms of desktop feel.

---

