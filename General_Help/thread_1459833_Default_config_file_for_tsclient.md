---
title: "Default config file for tsclient???"
date: 2010-04-22
forum: General Help
---

### Post by ingramproductions on 2010-04-22
Where is the config file for tsclient?
I want to change it so that when I open tsclient it is automatically set to a certain resolution, instead of defaulting to full screen (since rdesktop can't seem to use only 1 of the 2 screens in full screen mode).

Does anybody know where I can find this file?

---

### Post by zivley on 2010-04-28
tsclient is merely an frontend applet for rdesktop, vncviewer, wfica and xnest.
As soon as you run tsclient for the first time it will create the file ~/.tsclient/mru.tsc and when you close it will save the last used settings in ~/.tsclient/last.tsc
These settings are coming from the binary that runs the applet, no way to edit them.
You could instead edit the last.tsc and set whatever you like, or just config all the settings you want on the applet and then "Save As" and name it "Default.tsc" then next time you open it it will use the last session used.
Anyway, you won't be able to get all possible geometrics combination, I'd rather suggest you use "rdesktop" in command line.
For example:
```
rdesktop -g 1024x769 -u user -p password -d domain server:port
```
The -g option can accept also percent, for instance "-g 90%" will display a window at the 90 percent of your native resolution, without having to struggle with numbers and calculations...
You can create a launcher for this command and place it in your desktop.

---

