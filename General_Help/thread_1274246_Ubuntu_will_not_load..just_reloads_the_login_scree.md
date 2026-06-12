---
title: "Ubuntu will not load..just reloads the login screen"
date: 2009-09-24
forum: General Help
---

### Post by dazon22 on 2009-09-24
OK.. I am new to this forum so i will be a clear as possible.

Up until recently i was running Ubuntu 8.01 on a Lenovo 3000 N100. I was altering the CubeCompiz Settings for the desktop cube. I may have overloaded my systems graphical capabilities. As i was changing the settings, i immediatley crashed and was taken to my login screen..

after entering login/password the screen flashed my desktop background and then blacks out with random colors and takes me directly back to the login menu.

I tried to reboot, performed a file system check from the recovery menu, I tried to repair broken packages, as well as login from recovery mode. 

I would like to know if there is a way i can reformat my system from the terminal or root shell prompt.. if there is a solution that will save my data that would be ideal.. If i have to reformat my system that would also be acceptable.. Do i just burn a copy of the install 8.01 CD and start up with that..??

Thanks in advance for the help .. bear with me..!! :confused:

---

### Post by ajgreeny on 2009-09-24
Even though you may not be able to get into normal gnome, you may find that **failsafe gnome** from the Session options of the login screen is still available.  Use that and set your system to not use compiz, ie. none, from System ->Preferences ->Appearance in the menus.

You could login to command line and try ```
metacity --replace
```but I'm not sure that will do anything when not in a graphical mode.

If neither of those work, use the cli from recovery mode to remove compiz with ```
apt-get remove compiz
```Note, you will not need sudo for this in recovery mode.  You can then reinstall compiz after getting running again.

Another possibility to avoid uninstalling is to rename the /home/username/.gconf/apps/compiz folder again in cli mode with ```
mv /home/username/.gconf/apps/compiz /home/username/.gconf/apps/compiz.bak
```which will remove all configuration for compiz and should allow you to start again.

Good luck.  I hope one or other of these options is successful for you.

---

### Post by CatKiller on 2009-09-24
> **dazon22 said:**
>  I would like to know if there is a way i can reformat my system from the terminal or root shell prompt..

No need. Formatting to correct a window manager configuration problem is a walnut-sledgehammer solution.

From what I can gather, something you've done to your Compiz configuration is causing X to crash, and since Compiz is your default window manager, you get an X crash every time you log in, which means that you effectively can't log in to the desktop environment. All you need to do, then, is to change your default window manager, so that you can log in to your graphical environment and fix whatever you did to your Compiz configuration.

The most straightforward way to change the default window manager is to change the /desktop/gnome/applications/window_manager/current and ../default GConf keys. Unfortunately, you can't do this the easy way (gconf-editor) since you can't log in to the graphical environment. However, these keys are simply stored as XML files which can be edited using any text editor. Since you can't use a graphical text editor, you need a command-line one. Nano is quite easy to use.

You can log in on a virtual console to edit the XML file. Ctrl-Alt-F1 will take you to a virtual console (Alt-F7 will take you back to the graphical environment when you're done). If, for some reason, you can't get a virtual console (some weird combination of nVidia drivers, hardware and configuration appears to do this to some people) you can drop to a root shell from the Recovery Mode menu as you've done before.

You can edit the file with ```
nano ~/.gconf/desktop/gnome/applications/window_manager/%gconf.xml
``` (replace ~ with /home/*username* if you're using a root shell) and change the stringvalues to **/usr/bin/metacity**. Ctrl-O saves and Ctrl-X exits nano. Switch back to the graphical environment (or restart with *shutdown -r now* if you're in a root shell) and you should be able to log in again. Fix whatever it was that you broke, and then use **gconf-editor** (or the Appearance tool) to re-enable Compiz.

---

