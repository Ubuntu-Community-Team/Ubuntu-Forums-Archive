---
title: "Keyboard shortcut to keyboard shortcuts"
date: 2012-01-28
forum: General Help
---

### Post by krzysztofikus on 2012-01-28
Hi,

A short question, which I am unable to solve with google: I like to assign keyboard shortcuts to many actions I perform on my ubuntu. Each time an idea pops to my mind I have to navigate through System->Preferences->Keyboard Shortcuts. Is there any terminal command for direct access to the Keyboard Shortcuts menu?

I will appreciate any help.

---

### Post by Krytarik on 2012-01-28
First of all, the topic is quite hilarious, I must say! :popcorn::D
> **krzysztofikus said:**
> System->Preferences->Keyboard Shortcuts
Judging from that, I'm presuming you are running an Ubuntu version based on Gnome 2, so this would be the respective command:
```
gnome-keybinding-properties
```Btw., you can look up the command of any launcher you see in the menus (even if not) by exploring its respective .desktop file under "/usr/share/applications" or "~/.local/share/applications", respectively; therefore open it from inside (!) the text editor.

Regards.

---

### Post by krzysztofikus on 2012-10-11
Thanks! It worked, but after upgrade to 12.04 I have to look for a new solution. I know how to get to system settings (gnome-control-center command), but not how to get to keyboard shortcuts (or to e.g. brightness options).

---

### Post by vasa1 on 2012-10-11
I think this is a great question. Whether by a shortcut or not, it would be nice to have a list of all keyboard shortcuts in all contexts.

For example, I set up Control + Shift + Left Arrow in Openbox's rc.xml to "aero snap" forgetting that Control + Shift + Any Arrow is a basic way to highlight text if a text box is in focus.

---

