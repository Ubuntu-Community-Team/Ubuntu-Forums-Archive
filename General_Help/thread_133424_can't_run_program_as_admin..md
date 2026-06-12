---
title: "can't run program as admin."
date: 2006-02-20
forum: General Help
---

### Post by torx on 2006-02-20
i am trying to run gedit with *sudo* however, it doesn't open after a long wait.

so i did some googling and found this command *gksudo*

however, it doesn't seems to be working too. 

is this normal operation? only when trying to run **graphical** apps with admin in console does things seem to be borked, in other words, *sudo vi* or *sudo cp* and stuff works fine. 

> torx@Torx:~$ sudo gedit

(gedit:8203): Gdk-WARNING **: locale not supported by Xlib

(gedit:8203): Gdk-WARNING **: cannot set locale modifiers

** (gedit:8203): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:8203): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:8203): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:8203): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

(gedit:8203): GLib-GObject-WARNING **: invalid uninstantiatable type `GParamUInt64' in cast to `GObject'

(gedit:8203): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `GParamUInt64'

(gedit:8203): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:8203): GLib-GObject-WARNING **: invalid uninstantiatable type `GParamUInt64' in cast to `BonoboMDI'

** (gedit:8203): CRITICAL **: bonobo_mdi_add_child: assertion `BONOBO_IS_MDI (mdi)' failed

** (gedit:8203): CRITICAL **: gedit_file_new: assertion `ret != FALSE' failed
torx@Torx:~$



torx@Torx:~$ gksudo gedit

(gksudo:10097): Gdk-WARNING **: locale not supported by Xlib

(gksudo:10097): Gdk-WARNING **: cannot set locale modifiers

(gedit:10099): Gdk-WARNING **: locale not supported by Xlib

(gedit:10099): Gdk-WARNING **: cannot set locale modifiers

(gedit:10099): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


---

### Post by taurus on 2006-02-20
Try

sudo gedit

---

### Post by Lanrond on 2006-02-20
[QUOTE=torx]
is this normal operation? only when trying to run **graphical** apps with admin in console does things seem to be borked, in other words, *sudo vi* or *sudo cp* and stuff works fine.[/QUOTE]

I don't think that it generally applies to graphical apps. For example **sudo gvim** works well. It could be something about getid configuration. :???:

---

### Post by asbo on 2006-02-20
I've had a similar problem; the way I got around it was doing a [FONT="Courier New"]su[/FONT] which prompts you for the root password, and if you try and run whatever program again, it'll still give you an error, but it will actually launch -- everything that I've tried anyway.

Question, can you properly launch anything under System > Administration?

---

### Post by torx on 2006-02-21
wow, seems like this is a pretty common problem. 

> 
Question, can you properly launch anything under System > Administration?

Yeap, everything works fine.

> I've had a similar problem; the way I got around it was doing a su which prompts you for the root password, and if you try and run whatever program again

Yeap, it worked for me too. But the program took about 5 minutes to launch.

---

### Post by asbo on 2006-02-21
Very odd. I'm half tempted to wipe and install all over again.

Did you use the normal install or the expert?

---

### Post by torx on 2006-02-27
normal. i'm thinking that this might be a bug, but we'll need more inputs from other users.

---

### Post by asbo on 2006-02-28
Do you have the capacity to wipe and try with a fresh install? That's solved a couple issues for moi.

---

