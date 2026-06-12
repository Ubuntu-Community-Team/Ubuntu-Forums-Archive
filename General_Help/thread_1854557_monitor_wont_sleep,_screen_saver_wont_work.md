---
title: "monitor wont sleep, screen saver wont work"
date: 2011-10-04
forum: General Help
---

### Post by tobythedog on 2011-10-04
hi just installed xubuntu, i cannot get the screen saver to work and also the monitor will not sleep , help please

---

### Post by Toz on 2011-10-04
Since you don't mention what you've already tried, we can start from the beginning. Did you go to Settings->Settings Manager->Screensaver and enable/configure it?

Is xscreensaver running? Open a terminal (Accessories->Terminal Emulator), type the following in and post back the results:
```
ps -ef | grep xscreensaver | grep -v grep
```

---

### Post by tobythedog on 2011-10-04
cannot find the enable bit in settings there seems to be some problem as when i go there i get a warning. the xscreen saver deamon does not seems to be running on display 0 and i have the option to launch it now , when i click on this i get x screen deamon didnt start properly please check your $path and permissions.

---

### Post by Toz on 2011-10-05
Is xscreensaver installed? Look for it in the Software Centre or from the terminal window:
```
apt-cache policy xscreensaver
```

If not installed, then:
```
sudo apt-get install xscreensaver
```

If installed but not working, post back the contents of your **~/.xsession-errors** file right after you go to the screensaver settings and get the error message about it not starting.

---

