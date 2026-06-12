---
title: "Running compiz at login instead of metacity"
date: 2010-11-21
forum: General Help
---

### Post by Pollox on 2010-11-21
I would like to be able to use compizconfig-settings-manager to set some custom settings for compiz, and then have compiz be the window manager that runs when I log in. The trouble is that I cannot seem to find a good way to have compiz run at log in. I can add "compiz --replace" to my startup programs list, but this loads metacity and then replacing it with compiz and seem to add a bit to the startup time (not to mention it seems to be slightly unreliable).

Further, I tried this: Uninstalled compizconfig-settings manager. In appearance preferences, set visual effects to normal. Everything seems to work fine until I log in again, at which point *no* window manager runs. Setting visual effects to none makes metacity load.

Any ideas on this would be appreciated.

---

### Post by asmoore82 on 2010-11-21
Setting your desired level of Effects under "System -> Preferences -> Appearance"
Should "stick" and silently sets your preferred window manager.

The gconf key for this is "/desktop/gnome/session/required_components/windowmanager"

---

### Post by Pollox on 2010-11-22
Using the Effects level in Appearance preferences is correctly setting that gconf key, and that key value sticks even when logging in again. However, when the key value is compiz, no window manager starts at all.

Well, at least this narrows the issue down. It could be this bug: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/446566](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/446566), but I am not sure. Any idea which log file to look at that might indicate what is going wrong?

---

### Post by beew on 2010-11-22
Install the Compiz Fusion icon from the repository if you haven't already. To make Comiz auto start go to System > Preference > Startup Applications and click Add to create a startup entry for the Compiz Fusion icon.  On the name section you can put "Compiz Fusion  Icon" or anything really, for the command put  
```
fusion-icon --no-start
```

Next time when you boot Compiz should autostart.

---

### Post by Pollox on 2010-11-22
Hmm, I don't see the advantage of using fusion-icon unless I wanted the functionality it provides of switching window managers with an icon. But you do raise an interesting point. Now that I have confirmed that setting /desktop/gnome/session/required_components/windowmanager to "compiz" prevents metacity from starting, there shouldn't be any harm (in terms of startup time) in just using the "compiz" command in Startup Applications to start the window manager. It's not an ideal solution, but it will work for me in lieu of something better. Thanks for the ideas guys.

---

