---
title: "cairo-dock duplicating"
date: 2011-05-20
forum: General Help
---

### Post by eisenwyrm on 2011-05-20
Running Ubuntu 11.04

Added a custom script launcher to cairo-dock (no open).

When clicking custom script launcher, script launches succesfully.

Problem is with every click of said launcher, a dupe cairo-dock launches.

Script has nothing to do with cairo-dock.

Any ideas?

---

### Post by DanneStrat on 2011-05-21
> **eisenwyrm said:**
> Running Ubuntu 11.04

Added a custom script launcher to cairo-dock (no open).

When clicking custom script launcher, script launches succesfully.

Problem is with every click of said launcher, a dupe cairo-dock launches.

Script has nothing to do with cairo-dock.

Any ideas?

Could you post the contents of the script?

---

### Post by eisenwyrm on 2011-05-22
killall gnome-panel

---

### Post by DanneStrat on 2011-05-22
> **eisenwyrm said:**
> killall gnome-panel

Gnome-panel and cairo-dock offer similar functionalities, so the 

fact that you get a duplicate instance of cairo-dock when you 

kill gnome-panel may be a conflict between the two.

What do you want the script to accomplish?

If you would like to replace gnome-panel with cairo-dock, press

alt+f2 and type "gconf-editor" without the quotes and browse to 

the key "/desktop/gnome/session" and edit the 

"required_components_list" entry values.

By default it would look something like "windowmanager, panel, 

filemanager". Just delete the word "panel" from there and log out 

and back in again or just reboot and gnome-panel will be gone. 

Just add "panel" back in that entry if you want to reverse the 

process.

---

### Post by eisenwyrm on 2011-05-23
When I 1st upgraded to 11.04 with Unity, I lost my indicator applets from Gnome.

I 1st tried to set gnome-panel to start up with unity but this caused me problems in unity.

So I created a launcher for gnome-panel and placed it onto cairo-dock and the soon after created a script launcher to stop gnome-panel if/when it caused conflict within unity.

I have since discovered many replacement indicators for unity and finally got them to work properly. So I have no need for gnome-panel any more.

BUT

My question as to what causes this anomaly remains...

"killall gnome-panel" does not visually affect cairo-dock when executed in terminal nor when launched from a "script".

So why is cairo-dock affected by this when launched from the dock? (this may be an issue later on for any other scripts I may try to execute from a launcher placed onto cairo-dock)


**Side note: I have always used gnome-panel, awn, and cairo-dock together. They each have their strengths and weaknesses. Only now I have replaced Gnome with Unity. Tho not entirely sold on Unity yet.

---

