---
title: "Changed Screen Resolution to 800x600 and now cannot see display"
date: 2009-07-17
forum: General Help
---

### Post by Terry of Astoria on 2009-07-17
I wanted to temporarily change my resolution to 800x600 for a game and I didn't realize that -1. My monitor can't display the res that I chose; and -2. Ubuntu 8.10 resolution picker no longer gives me the "are you sure you want to use this resolution- reverting xx seconds . . ."
  So now I don't know how to restore my display. It's still running my game (I can hear it) but now the screen is black, with the monitor saying "cannot display blah blah..." I can go to another console, like <ctrl-alt-f4>. Is there a hotkey, or a command I can give from the console to set the res back to 1024x768 or higher? Will I have to reboot and perhaps somehow reconfigure the X-server?

---

### Post by litspliff on 2009-07-17
once you get to your console, use "sudo vi" to edit your xorg.conf file. more info can easily be found on google.

don't forget to restart your X after you save.

---

### Post by CatKiller on 2009-07-17
Crikey. Changing the xorg.conf for the per-user resolution is overkill, and suggesting vi is just evil :twisted:

You could probably use something like ```
xrandr --mode 1024x768
``` to change the resolution to 1024×768 (I haven't used xrandr, so there might need to be something else in there too, like --screen 0).

Otherwise, the per-user resolution is stored in ~/.config/monitors.xml. You could modify/move/delete that file and restart the X server to use a default resolution for that user.

---

