---
title: "no apps in dash"
date: 2012-01-02
forum: General Help
---

### Post by maxlit on 2012-01-02
Hello everyone,
I'm facing the following problem.

All of the sudden (maybe after installing synaptics, not sure), the apps in dash (ubuntu 11.10) have disappeared (click on dash, then "Media apps" -> nothing).
Besides, in order to launch the software center, I have to type in terminal "sudo software-center" (without sudo it doesn't work) and not just to click on the left icons bar.
I appreciate every advice.

---

### Post by saneearth on 2012-01-02
Try ALT F2, then enter the command "unity --reset" and see if that fixes your issue. I doubt installing synaptic had anything to do with it, but your Unity settings are definitely messed up. Hopefully, this will reset things to default for you and you can go from there.

---

### Post by maxlit on 2012-01-02
> **saneearth said:**
> Try ALT F2, then enter the command "unity --reset" and see if that fixes your issue. I doubt installing synaptic had anything to do with it, but your Unity settings are definitely messed up. Hopefully, this will reset things to default for you and you can go from there.

thanks for the advice, unfortunately it didn't work out.

let me quote the output of this action (some things are missing, I don't know how crucial they are):
> 

WARNING: Unity currently default profile, so switching to metacity while resetting the values

(metacity:2219): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:2219): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:2219): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:2219): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done
WARN  2012-01-02 18:37:41 glib.glib-gobject <unknown>:0 invalid (NULL) pointer instance

Screen geometry changed:
   0x0x1680x1050

unity-panel-service: no process found
Initializing unityshell options...done
WARN  2012-01-02 18:37:42 unity.favorites FavoriteStoreGSettings.cpp:138 Unable to load GDesktopAppInfo for 'ubiquity-gtkui.desktop'
WARN  2012-01-02 18:37:42 unity.favorites FavoriteStoreGSettings.cpp:121 Unable to load desktop file: /home/lab/Desktop/xd0x93xd0xb0xd0xbcxd0xb1xd0xbbxd0xb5xd1x80-1325418608395.desktop
DEBUG 2012-01-02 18:37:42 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1680 h=1050
Initializing staticswitcher options...done
Setting Update "main_menu_key"
Setting Update "run_key"
WARN  2012-01-02 18:38:41 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2012-01-02 18:38:41 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2012-01-02 18:38:41 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2012-01-02 18:38:41 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2012-01-02 18:38:43 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-01-02 18:38:43 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-01-02 18:38:43 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-01-02 18:38:43 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-01-02 18:38:43 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2012-01-02 18:38:43 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory

(firefox:2415): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:2415): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:2415): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:2415): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(plugin-container:2458): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(plugin-container:2458): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(plugin-container:2458): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(plugin-container:2458): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",



---

### Post by maxlit on 2012-01-02
now, the apps appeared again. i don't understand why, since I actually tried "unity --reset" and even "unity -reinstall" before posting here, and restarted my PC several time since then.

my hypothesis now that it intervenes in some way with mysql processes. i had this after working with mysql db, now i sent the query to mysql DB and now I have apps in dash again. It must be coincidence.

---

