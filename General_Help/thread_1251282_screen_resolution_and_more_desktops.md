---
title: "screen resolution and more desktops"
date: 2009-08-27
forum: General Help
---

### Post by tinker88 on 2009-08-27
so my fiance said that it was cario-dock that was crashing compiz ....but now i only have 2 desktops instead of 4 like i did before ...i can live without cario dock but i would really like to have the 4 desktop cube back 
 
i tried a couple of different things and had no results. 
 
one discussion said to go into the advanced desktop effects settings>general options>desktop size and change the horizontal virtual size to 4 and that did nothing 
 
i also tried to reinstall all the compiz config stuff and emerald after that it told me to click alt + F2 and type compiz --replace and when i did that the terminal opened and said : 
 
 
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
/usr/share/themes/Clearlooks-Cairo-Pink/gtk-2.0/gtkrc:56: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/Clearlooks-Cairo-Pink/gtk-2.0/gtkrc:57: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/usr/share/themes/Clearlooks-Cairo-Pink/gtk-2.0/gtkrc:58: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2800081 (Synaptic P)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400020 (Terminal)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x24001cb (Xubuntu + )
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400020 (Terminal)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
 
 
 
 
then when i enabled the nvidia accelerated graphic card and restarted the whole screen is doubled in size and now i dont know how to get back to normal 
 
 
please someone help me
 
thank you

---

### Post by uylug on 2009-08-27
> **tinker88 said:**
> so my fiance said that it was cario-dock that was crashing compiz ....but now i only have 2 desktops instead of 4 like i did before ...i can live without cario dock but i would really like to have the 4 desktop cube back 
 
i tried a couple of different things and had no results. 
 
one discussion said to go into the advanced desktop effects settings>general options>desktop size and change the horizontal virtual size to 4 and that did nothing 
 
i also tried to reinstall all the compiz config stuff and emerald after that it told me to click alt + F2 and type compiz --replace and when i did that the terminal opened and said : 
 
 
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
/usr/share/themes/Clearlooks-Cairo-Pink/gtk-2.0/gtkrc:56: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/Clearlooks-Cairo-Pink/gtk-2.0/gtkrc:57: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/usr/share/themes/Clearlooks-Cairo-Pink/gtk-2.0/gtkrc:58: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2800081 (Synaptic P)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400020 (Terminal)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x24001cb (Xubuntu + )
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3400020 (Terminal)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
 
 
 
 
then when i enabled the nvidia accelerated graphic card and restarted the whole screen is doubled in size and now i dont know how to get back to normal 
 
 
please someone help me
 
thank you

Hello, you can clear your Compiz settings like this
```
rm .compiz -r
rm .config/compiz -r
```As for the Nvidia Drivers i suggest disabling the drivers via the System -> Administration -> Hardware drivers menu and then download the latest drivers from the NVIDIA Website

What is your graphics card model?

---

### Post by tinker88 on 2009-08-27
im honestly not sure what graphics card model i have....but if you can tell me how to find out i can do so.....im still new to a lot of this computer stuff and linux ...but im trying to learn as quickly as i can 
 
as far as the nvidia stuff....i already went back into the hardware drivers and unchecked the nvidia accelerated graphic card and clicked to disable it but when i rebooted and went back into hardware drivers it showed it being unchecked but next to it it still had a green circle and said in use 
 
thank you for your help

---

### Post by hyperdude111 on 2009-08-27
If you want your desktop cube back go to

System-Preferences-CompizConfigSettingsManager

Go to the general option.
Go to Desktop size tab
Change it to 4

---

### Post by tinker88 on 2009-08-27
> **hyperdude111 said:**
> If you want your desktop cube back go to
 
System-Preferences-CompizConfigSettingsManager
 
Go to the general option.
Go to Desktop size tab
Change it to 4
 
 
i already tried that prior to my original post and it did nothing
 
thanks

---

### Post by kerry_s on 2009-08-27
menu-> settings-> workspaces ?

---

### Post by tinker88 on 2009-08-27
> **kerry_s said:**
> menu-> settings-> workspaces ?


tried this now .... changed it from 2 to 4 and still only have 2 desktops

also i went back into my windows (comp is dual booted with windows and linux) and tried to find out my graphics card model .

display properties settings says "NVIDIA GeForce 8400M GS


thanks

---

