---
title: "Changing resolution in VMware"
date: 2006-05-06
forum: General Help
---

### Post by yang on 2006-05-06
I installed 5.10 on VMware but I can't change the screen resolution (I'd like to lower it).

During installation, I was presented with a list of screen resolutions. 1024x768, 800x600, and 640x480 were checked by default. I additionally checked 1280x1024; I only wanted this there as an option, not as the default. However, 1280x1024 became the default.

I went to Preferences > Screen Resolution and tried lowering the res, but then my screen becomes garbled (have to wait for the timeout for the resolution to revert).

I then tried editing /etc/X11/xorg.conf (changed the DefaultDepth from 24 to 16). Then I logged out, hit ctrl-alt-backspace, logged in, and tried again to change Preferences > Screen Resolution, to the same result. This solution (changing the color depth) also doesn't make much sense to me - wasn't Gnome originally operating at 24-bit color, only in higher res?

Please help, thanks in advance.

Related URLs:

DefaultDepth change suggested here:

[http://ubuntuforums.org/showthread.php?t=124543&highlight=vmware+resolution](http://ubuntuforums.org/showthread.php?t=124543&highlight=vmware+resolution)

These don't seem to apply to my situation (I'm trying to lower the color depth; my monitor is 'generic'; also suggested DefaultDepth change; not using ATI or Intel Graphics:

[https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

---

### Post by Computeruser on 2006-05-06
Ubuntu is a VMware virtual machine - right?  Did you then install the VMware Tools? You need to do that for the display (and other things) to work properly. This is because VMware provides its own "hardware". Once the Tools are installed, I see in my xorg.conf file a section near the bottom where the resolution gets set (under Device VMware SVGA). It also warns you in there not to change Colour Depth.

---

### Post by ferdush on 2006-06-09
can you please explain which vmware tools you mean to install? My VMWARE WORKSTATION is on WinXp and I installed Ubunon on it. Resolution is so high and unchangable that I've scroll all times to click on statup menu. Do we need to install VMWARE tools on Ubuntu? I am new with linux and disregard if I misunderstand.
-Ferdush

---

