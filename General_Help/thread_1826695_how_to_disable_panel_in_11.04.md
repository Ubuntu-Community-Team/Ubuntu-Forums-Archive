---
title: "how to disable panel in 11.04?"
date: 2011-08-16
forum: General Help
---

### Post by princeofnam on 2011-08-16
I used to be able to follow these instructions prior to upgrading to 11.04 

"
**Step 4 €“ Remove gnome-panel**

 Open up Gconf editor by hitting Alt + F2 and typing *gconf-editor*
 Using the tree view on the left, navigate to desktop -> gnome  -> session -> required_components -> panel and change  “gnome-panel” to “avant-window-navigator” (ignoring quotation marks of  course!)
 Log out and back in just to make sure, and everything should be working swell!
 If it doesn’t work for you, you can always go back by opening up a terminal (Ctrl + Alt + T) and lauching *gconf-editor* then changing the value above back to gnome-panel. Log out and back in again by using the command *sudo service gdm restart* in a terminal."




I'm trying to revert back to just an AWN type panel.  However, when I try to go to the panel setting under required_components, I don't see it.  Does anyone know what happened?

---

