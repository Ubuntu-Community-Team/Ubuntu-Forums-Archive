---
title: "Changing by itself"
date: 2012-04-09
forum: General Help
---

### Post by Kheldragar on 2012-04-09
It`s weird. After waking up, I find the style for just about everything has changed to what seems to be a Windows 2000 colour scheme. It`s also spread to Firefox as well (In certain buttons and that dropdown menu when you enter an address which won`t let me take a screenshot of it). Does anyone know how I can change back to my orange, default one?
[[IMG]http://img515.imageshack.us/img515/2421/screenshotat20120409031.png[/IMG]]("http://imageshack.us/photo/my-images/515/screenshotat20120409031.png/")

[U][[IMG]http://img801.imageshack.us/img801/6272/screenshotat20120409032.png[/IMG]](http://imageshack.us/photo/my-images/801/screenshotat20120409032.png/)
[/U]
[[IMG]http://img513.imageshack.us/img513/2421/screenshotat20120409031.png[/IMG]]("http://imageshack.us/photo/my-images/513/screenshotat20120409031.png/")

---

### Post by Frogs Hair on 2012-04-09
Nautilus draws the desktop so restarting Nautilus should restore the theme , but I don't know the cause . The problem was supposed to have been addressed with an update quite a while ago. Try the following.```
nautilus -q
```

---

### Post by Kheldragar on 2012-04-09
> **Frogs Hair said:**
> Nautilus draws the desktop so restarting Nautilus should restore the theme , but I don't know the cause . The problem was supposed to have been addressed with an update quite a while ago. Try the following.```
nautilus -q
```

Here`s what I get.

```
daimon@daimon:~$ nautilus -q
Initializing nautilus-gdu extension
** (nautilus:25319): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(nautilus:25319): Gtk-CRITICAL **: gtk_action_set_visible: assertion `GTK_IS_ACTION (action)' failed

(nautilus:25319): Gtk-CRITICAL **: gtk_action_set_visible: assertion `GTK_IS_ACTION (action)' failed

--- Hash table keys for warning below:
--> daimon
--> Daimon
--> l2049
--> inode/directory

(nautilus:25319): Eel-WARNING **: "unique eel_ref_str" hash table still has 4 elements at quit time (keys above)

--- Hash table keys for warning below:
--> file:///home/daimon
--> file:///home/daimon/Desktop
--> x-nautilus-desktop:///

(nautilus:25319): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 3 elements at quit time (keys above)
Shutting down nautilus-gdu extension
daimon@daimon:~$ 

```

---

### Post by Frogs Hair on 2012-04-09
Sorry , I not sure what is happening there the command is to restart nautilus and I can't reproduce the output. I get no warnings when restarting nautilus.

---

### Post by AlexOnVinyl on 2012-04-09
If you cant seem to figure out what's causing the issue, your best bet at making sure things are fixed is to switch desktop environments, then uninstall gnome3 and reinstall even if that doesn't help then I'd say just go back to gnome classic/fallback

[B]TL;DR

either switch desktop environments & reinstall gnome or reinstall system all together - of course the latter is only if its really really needed.[/B]

---

