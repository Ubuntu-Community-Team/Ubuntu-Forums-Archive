---
title: "MATLAB replaced my gnome-terminal icon!"
date: 2010-09-22
forum: General Help
---

### Post by yunchiluo on 2010-09-22
I created a menu entry to run MATLAB using
```
 gnome-terminal -x /usr/local/bin/matlab
```

After using MATLAB a few times, I realized that my gnome-terminal icon has actually been replaced with the MATLAB icon, even when I'm running the terminal by itself. Meaning that it shows the MATLAB icon in the taskbar and the Run Applications dialog when I type in gnome-terminal.

Reinstalling gnome-terminal did not fix this. While this is not a critical issue, I would appreciate help to get the icon back to normal.

---

### Post by JC Cheloven on 2010-09-22
This is stored in the PS1 variable. Try this:

```
PS1='\u@\h:\W \$'
```

---

### Post by JC Cheloven on 2010-09-23
Oops, sorry, in a second read I think you meant the graphical icon in the user interface, not the shell prompt.

You can change the icon comfortably using the user interface: please open system-preferences-main menu. 
Once there, search for the terminal inside the acesories menu (my explanation seems like recursive, but it's ok). Select it and press properties. 
In the popup window, click on the icon at the top left. You'll be presented with several icons lying in a folder. You can browse (eventually) other folders containing icons. The default incon for the terminal should be:

/usr/share/icons/gnome/scalable/apps/utilities-terminal.svg  # was for karmic
or
/usr/share/icons/Humanity/apps/48/utilities-terminal.svg # default for lucid
or something.

Hope to be of help this time ;)

---

### Post by yunchiluo on 2010-09-23
JC, thanks for your reply, but my problem is much more peculiar than that. The terminal icon in the main menu is actually the correct gnome terminal icon, while the icon that gets displayed in the taskbar (window list), when terminal is running, and in the run applications dialog (Alt+F2) is the MATLAB icon.

---

