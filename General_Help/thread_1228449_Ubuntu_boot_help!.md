---
title: "Ubuntu boot help!"
date: 2009-07-31
forum: General Help
---

### Post by Buuntu on 2009-07-31
After installing some drivers needed for my wireless network card, following these instructions : [https://help.ubuntu.com/community/WifiDocs/DWL-G510](https://help.ubuntu.com/community/WifiDocs/DWL-G510), my system won't boot right.  I mean, it boots to gnome and all, but I can't click on anything, there are no icons on the panels, and several commands don't work in the terminal (the terminal does work).  I already tried uninstalling ndiswrapper with sudo modprobe -r ndiswrapper and sudo apt-get remove ndiswrapper-common, but neither of them did anything - they just sent the cursor to a new line.  I should also add that when i shutdown, ubuntu tell me that the panel, file manager, update notifier, and beagle search tool are still running but not responding.  Help me please, I do not want to reformat.

ndiswrapper -l:
```
Warning: ALL config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release
Warning: All config. files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release
mrv8k51: driver installed           
             device (11AB:1FA6) present
metrt61G : driver installed
```[SIZE=2]
[/SIZE][SIZE=2]
[/SIZE]

---

### Post by Buuntu on 2009-08-01
bump

---

### Post by Buuntu on 2009-08-03
bump

---

