---
title: "How I resolved my Firefox1.5 plugin issue"
date: 2006-04-03
forum: General Help
---

### Post by japs_it88 on 2006-04-03
I installed the newest Firefox 1.5 on Breezy, following this tutorial:[https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefoxnew%29]("https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefoxnew%29").
  Since Synaptics install new plugins in the old firefox version's folder, they don't work in the newer, though one of the steps of the tutorial consists of linking the new Firefox with the old plugins. That didn't work because in /opt/firefox there is already a directory 'Plugins'.

   You can bypass the problem by renaming /opt/firefox/plugins to /opt/firefox/plugins_backup and run the following code in a terminal:
```
cd /opt/firefox
sudo ln -s /usr/lib/mozilla_firefox/plugins
```

---

### Post by aysiu on 2006-04-03
The tutorial's always worked for linking the plugins folder to /usr/lib/mozilla-firefox/plugins as far as I've seen...

This is what's supposed to do it: ```
cd /opt/firefox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/* .
sudo rm libtotem_mozilla.*
``` When you copied and pasted commands from the Wiki, did you include the * and the . at the end?

---

### Post by japs_it88 on 2006-04-03
[QUOTE=aysiu]The tutorial's always worked for linking the plugins folder to /usr/lib/mozilla-firefox/plugins as far as I've seen...

This is what's supposed to do it: ```
cd /opt/firefox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/* .
sudo rm libtotem_mozilla.*
``` When you copied and pasted commands from the Wiki, did you include the * and the . at the end?[/QUOTE]


It didn't work for me because 

sudo ln -s /usr/lib/mozilla-firefox/plugins/*

returned that the argument of a multiple link must be a folder, thus created a subdirectory-like link in /opt/firefox/plugins. That didn't work for me and the browser was unable to use the so linked plugins.

---

### Post by aysiu on 2006-04-03
You need to include the period, too, not just the asterisk.

---

