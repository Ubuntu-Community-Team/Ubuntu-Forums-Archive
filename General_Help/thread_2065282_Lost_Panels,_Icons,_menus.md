---
title: "Lost Panels, Icons, menus"
date: 2012-10-01
forum: General Help
---

### Post by SuperFreak on 2012-10-01
I was trying to get screensavers to work in  Cinnamon 1.6 Ubuntu 12.04 with disastrous results. After installing and uninstalling xscreensaver and gnomescreensaver a few times my desktop is wrecked. I have no menu, panels , icons or terminal (I can summon terminal with CTL-ALT-T but can't enter commands). Firefox and Thunderbird open on startup as they usually do but the option to minimize,maximize or close the window is gone.

Help would greatly be appreciated

edit; maybe this suggests the problem. If I place the cursor on the desktop it displays as an X rather than the usual arrow. Tried reinstalling Cinnamon with sudo apt-get purge cinnamon && sudo apt-get install cinnamon after CTRL+ALT+ F1 no luck though

edit 2: OK another stab in the dark due to my impatience. Tried CTL+ALT+F2 followed by ```
sudo apt-get update
``````
sudo apt-get install gnome-panel
``` no luck

---

### Post by SuperFreak on 2012-10-01
Removing Cinnamon using code ```
sudo apt-get remove cinnamon
``` brings me back to a working XFCE desktop. I would really like to get Cinnamon back without all the problems I created. Is there a safe way?

---

### Post by SuperFreak on 2012-10-01
[http://www.linuxbsdos.com/2012/09/20/install-cinnamon-1-6-in-ubuntu-12-04-lts/]("http://www.linuxbsdos.com/2012/09/20/install-cinnamon-1-6-in-ubuntu-12-04-lts/")

Link helped me reinstall Cinnamon. seems to be working properly now

---

