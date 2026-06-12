---
title: "Graphic display problem displaying old theme in Ubuntu 11.04 using VirtualBox"
date: 2011-04-28
forum: General Help
---

### Post by abcuser on 2011-04-28
Hi,
today I have installed Ubuntu 11.04. On my computer there is not possible to have a Unity (graphic card not supported), so I have installed Unity 2D from PPA.

What I don't like is the look of the theme I got by default. If I remember correctly from previous versions of Ubuntu this theme was always displayed when something went wrong at boot time. So now I have rebooted Ubuntu and the theme has not changed.

See attached picture of Firefox (arrow shows to a help icon). I think this should not be a default theme and there is very likely that in my case there is something wrong. How to change a theme in Ubuntu 11.04?
Thanks

---

### Post by coldraven on 2011-04-28
I don't know but according to this link you will have less options
[http://www.omgubuntu.co.uk/2011/03/unity-2d-a-quick-look-at-the-latest-updates/](http://www.omgubuntu.co.uk/2011/03/unity-2d-a-quick-look-at-the-latest-updates/)

---

### Post by abcuser on 2011-04-28
I don't think this is Unity 2D problem at all. The problem appeared right away after first reboot when I got message that Unity can't be used and Ubuntu Classic was loaded. This "default" theme was there already before I have installed Unity 2D. So I think this is general Ubuntu problem and not some specifics to Unity 2D.

Any idea how to solve this problem? How to change a theme?

---

### Post by Magnes on 2011-04-28
I had this problem in VirtualBox. I found a way - deleted the machine and never looked back. :confused: Right know I'm afraid to update to 11.04.

---

### Post by 3Miro on 2011-04-28
Unity (2/3D) runs on top of Gnome2. Thus you change the theme the same way you would on Gnome2. From the menu, look for Appearance and you can change the theme.

Unity requires a 3D capable video card. Check the additional drivers section (search for it in the menu) to see if you simply need a new driver. If your machine is old, it may not support 3D effects (pretty much anything new would work fine).

In order to run Unity under Virtual Box, you need a 3D driver for Virtual Box (which is tricky business). Virtual Box that comes with Ubuntu 10.10 doesn't support Xorg 1.10, which comes with 11.04. In order to run 11.04 under Virtual Box, you need to install the latest Virtual Box from their web-page (then install guest addons, then enable 3d effects).

---

### Post by abcuser on 2011-04-29
> **Magnes said:**
> I had this problem in VirtualBox. I found a way - deleted the machine and never looked back. :confused: Right know I'm afraid to update to 11.04.
I use Windows XP sp3 as host and Ubuntu 11.04 as guest in VirtualBox 4.0.6 which is the latest release from virtualbox.org web page. This is the first time this problem appeared. I have been using Ubuntu since Edgy under VirtualBox and not having this problem before.

---

### Post by abcuser on 2011-04-29
> **3Miro said:**
> Unity (2/3D) runs on top of Gnome2. Thus you change the theme the same way you would on Gnome2. From the menu, look for Appearance and you can change the theme.
I have checked this and only title bar and close, min and max buttons changes, but the rest of the window does not change. It looks like this is not a theme problem.

> **3Miro said:**
> Unity requires a 3D capable video card. Check the additional drivers section (search for it in the menu) to see if you simply need a new driver. If your machine is old, it may not support 3D effects (pretty much anything new would work fine).Unity 3D will not work on my laptop. I have reported a bug for VirtualBox few years ago related to 3D and the problem is my system. In order to any 3D graphics to work under VirtualBox you need to have:
1. hardware to support 3D
2. host operating system that supports 3D
3. host (in my case Windows) software graphical drivers that supports 3D
4. VirtualBox version that does support 3D
5. guest operating system that supports 3D
6. set all the settings in VirtualBox (like 3D checkbox)
Problem in my case is No. 3, I have an Intel graphic driver for Windows that does not support 3D rendering. So in this case Unity 3D running inside my Windows XP will NEVER run. If I would like to have Unity 3D, I need to change host operating system (to get newer version of Intel graphical card drivers), but I don't have any business reason to do this change.

> **3Miro said:**
> In order to run Unity under Virtual Box, you need a 3D driver for Virtual Box (which is tricky business). Virtual Box that comes with Ubuntu 10.10 doesn't support Xorg 1.10, which comes with 11.04. In order to run 11.04 under Virtual Box, you need to install the latest Virtual Box from their web-page (then install guest addons, then enable 3d effects).I know all this, but as I said before my Windows graphic card driver is no good.

---

### Post by abcuser on 2011-04-29
This "ugly theme problem" is actually a problem with VirtualBox graphic card driver. I have solved the problem. I have written the details on Virtualbox forum theme [Graphic display old theme problem in Ubuntu 11.04.](http://forums.virtualbox.org/viewtopic.php?f=6&t=41127&p=185018)

---

