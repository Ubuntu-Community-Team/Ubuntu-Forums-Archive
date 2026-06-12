---
title: "my screen resolution is Locked at 648x480"
date: 2006-01-30
forum: General Help
---

### Post by paulharper on 2006-01-30
i turned on my computer today and it is locked at this low resolution. it will not allow for me to change it back. what info is needed and what should i do to fix this. 

thankyou

---

### Post by dcstar on 2006-01-30
[QUOTE=paulharper]i turned on my computer today and it is locked at this low resolution. it will not allow for me to change it back. what info is needed and what should i do to fix this. 

thankyou[/QUOTE]
In a terminal:

sudo dpkg-reconfigure xserver-xorg

and let it redetect your settings, then reboot.

---

### Post by deathshadow on 2006-01-30
Ah, this problem... This one comes up so often you'd think they'd simplify the process or sticky a howto.

Two ways of dealing with this:
Method #1 (for those intimidated by text editors)
open up a terminal, type

*dpkg-reconfigure xserver-xorg*

Most of the options should already be set correctly, when you get to the monitor section, choose medium - NOT simple or advanced. Just pick a monitor with the max resolution/refresh rate you want, select all the video modes you want. This is the part most people don't clarify on - and let's face it, the average user doesn't know @#$% about refresh rates, and the 'simple' version is damn near useless.

Once you've finished the reconfigure, logout and at the GDM login screen hit ctrl-alt-backspace, and GDM should auto-reload X at the new resolution... saves you from wasting time rebooting.

Method #2 edit your /etc/X11/xorg.conf to change the rates in the monitor section to read:

HorizSync 20-95
VertRefresh 30-120

which should 'unlock' damn near any mode you want. Down in the screens section you should make sure all the modes you want are listed in the color depths you want to run. (I generally delete the modes I'm not going to use).

Logout, ctrl-alt-backspace, new resolutions should be available.

---

