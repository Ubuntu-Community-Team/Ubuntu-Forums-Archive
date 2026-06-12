---
title: "unlocked software center from launcher - how do I get it back?"
date: 2012-03-10
forum: General Help
---

### Post by mastermesh on 2012-03-10
unlocked software center from launcher - how do I get it back?  I'm pretty new to Ubuntu.  I tested it a few versions back, but with 12 things are a bit different... Still trying figure out the gui.  I think I like it but have no idea how to get the software center thing back.  I can see it in dash if I search for it, but I can't click on it...?!?

Also, is there any way to lock stuff so that you can't accidentally unlock it from launcher?  Also how do you get force quit icon on screen?  I used to use that a lot to make stuff stop if it acted up.

Also... Geesh, I have so many n00b questions, lol... How do you get to where you can see the whole hard drive and all the partitions and stuff?  I have 2 250 gig hard drives on this machine and it seems like ubuntu only sees one of them?  Thinking maybe the other needs to be partitioned if it's not right now or something, but I have no idea how to get in to that sort of thing to figure it out?

---

### Post by mastermesh on 2012-03-11
well installed synaptic and put it on the launcher, but still can't seem to get sofware center back on there or get it to open now?!?,...

---

### Post by raja.genupula on 2012-03-11
Hi open software center and then it will be in launcher , then at launcher only give a rightclcik at software center and select as keep in Launcher .

---

### Post by stinkeye on 2012-03-11
For a force quit icon in the launcher,
paste this in gedit and save as **X-Quit.desktop** in **~/.local/share/applications**
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_AU]=gnome-panel-force-quit
Name[en_AU]=X-Quit
Exec=sh -c 'notify-send "Click on an application to force-close it, or right-click to cancel."; xkill'
Comment[en_AU]=Click on the app to quit
Name=X-Quit
Comment=Click on the app to quit
Icon=gnome-panel-force-quit
```
Then just drag and drop the X-Quit.desktop file to the launcher.

---

### Post by mastermesh on 2012-03-12
drag it using which file manager?  Konqueror won't let me, and the default one has it hidden?

---

### Post by stinkeye on 2012-03-13
ctrl+h to show hidden.
or type X-Quit in the dash and drag from there.

---

