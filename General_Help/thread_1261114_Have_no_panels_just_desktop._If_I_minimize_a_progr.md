---
title: "Have no panels just desktop. If I minimize a program I cant get it back???"
date: 2009-09-08
forum: General Help
---

### Post by rock it on 2009-09-08
Hi,
I recently was having trouble with graphic settings not saving properly so I was advised to do the following

alt+F2

then in the run menu type "gksu nvidia-settings" this way I managed to save the graphics settings.

[http://ubuntuforums.org/showthread.php?t=1060440](http://ubuntuforums.org/showthread.php?t=1060440)

I got the info from that thread.

When I rebooted the login screen looked promising, It was at the right resolution etc. But when I logged in I noticed there wasn't any panels at the top or bottom???

I checked to see if they were just hidden but there not. I can't change the panel settings, the panel settings dont load up when I click, so now whenever I minimize a window I cant get it back.

Thanks for any help.

---

### Post by sideaway on 2009-09-08
short solution would be alt+tab, this will allow you to cycle minimised windows in the short run, however, is the gnome environment still installed?

EDIT: Just saw you use xubuntu, sorry, ignore the gnome environment comment, I have little expereince with Xubuntu, better wait for a more experienced member help with this one

---

### Post by Simian Man on 2009-09-08
Open a terminal and run the command
>xfce4-panel&

That will hopefully relaunch your panels.

Also in Xfce, by default, if you middle click on the desktop you will get a list of opened windows.

---

### Post by rock it on 2009-09-08
I checked and I have a ".Gnome2" folder and ".Gnome2_private"

can't remember if I used to have just a ".gnome" folder aswell. Thanks I don't have to be scared of minimizing stuff now :P.

I'll keep working at it, and googleing.

---

### Post by rock it on 2009-09-08
Here's what the terminal says:

:~$ >xfce4-panel&
[1] 5848
[1]+  Done                     > xfce4-panel
:~$

but there's still no panels thanks though,

please, keep it coming

---

### Post by vambo on 2009-09-08
Do the same thing with Run Program.
That is: Alt F2, then type in
```
xfce4-panel
```
then Run.
You should now have your panel(s).
To make sure you always have them:
In Session and Startup, make sure you have "Automatically save session on logout" checked.

---

### Post by rock it on 2009-09-08
I typed it in wrong. The panels are now working but if I close the terminal then they go away again.

thanks though.

---

### Post by rock it on 2009-09-08
sorry about al the posts heres what the terminal says again:

:~$ 
(xfce4-mixer-plugin:6195): libxfce4mixer-CRITICAL **: xfce_mixer_get_track: assertion `GST_IS_MIXER (card)' failed

(xfce4-mixer-plugin:6195): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_card: assertion `GST_IS_MIXER (card)' failed

(xfce4-mixer-plugin:6195): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_track: assertion `GST_IS_MIXER_TRACK (track)' failed

---

### Post by rock it on 2009-09-08
I have tried using run and terminal but whenever I go to logg out it closes the panels instead and doesnt shutdown. I know I can shut down using right click on the desktop, just not working yet.

Thanks.

Any more ideas??

---

### Post by rock it on 2009-09-08
Ok, I know whats wrong so anyone got any ideas. My gnome panel folder has been deleted so does anyone know how to replace it? is there a way?

---

