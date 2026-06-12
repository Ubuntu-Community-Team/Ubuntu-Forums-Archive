---
title: "Settings not Saving in Ubuntu"
date: 2011-06-28
forum: General Help
---

### Post by CrusaderAD on 2011-06-28
Ok, let me explained what I did. I was curious and decided to try out Gnome 3. Big mistake. I did a purge to get rid of it and now Unity comes back up. So far so good. Now none of my settings save... my "keep in launcher" apps do not stay there, my settings (accounts work fine) in Empathy don't stay and the weather settings reset. How do I get things to save when logging out or rebooting?

---

### Post by mcduck on 2011-06-28
First thing to do would be checking that all the file and directory permissions and ownerships) in your home are correct.

Anyway, such settings are not saved when you log out, they are saved immediately when you change a setting, and failing to save them is usually a permission problem.

Starting a program from a terminal would probably also give you better information about any problems that occur when running it.

---

### Post by CrusaderAD on 2011-06-28
Thanks for the update. The settings do save when I first make the change in the program. Here's what I got when I launched empathy from the terminal:

> GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.


---

### Post by CrusaderAD on 2011-06-29
Another update, not sure if this helps... sometimes clicking on a Unity launcher will launch another instance of the program rather than bringing up the window.

---

### Post by tjeremiah on 2011-07-04
same problem as the TC, everything is now ROOT! How do I revert back to the old way of doing things (doing simple things like adding a program to the launcher without having to go root) ?

Every time I go and change/remove a program in the launcher, I log out, and nothing has changed. When I look at the programs/applications, it tells me I am not the owner, I cannot change settings.

---

