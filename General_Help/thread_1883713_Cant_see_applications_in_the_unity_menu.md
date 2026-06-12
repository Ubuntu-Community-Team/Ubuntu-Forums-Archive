---
title: "Cant see applications in the unity menu"
date: 2011-11-19
forum: General Help
---

### Post by akshay.sulakhe on 2011-11-19
Hello friends, I have latest Ubuntu 11.10(32 bit) installed on my desktop. When i go in the upper left corner menu,which is called as dash home if u hover over it,i cant see any applications even when i search it or even i go in media apps,other apps,anything. Nothing,i have to open all applications via the terminal. Kindly let me know what to do to get it back. Many thanks... :-)

---

### Post by cariboo on 2011-11-19
Have you tried:

```
unity --reset
```

in a terminal? The above command should set things back to way they were, the first time you logged into Unity.

---

### Post by akshay.sulakhe on 2011-11-19
I tried it now,it didnt work..i will post everything that it showed on console when i gave the command,i gave it as non root or without sudo,i hope thats ok

Log of command unity --reset (Its a big log) :-

akshay@akshay-desktop:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values

(metacity:14624): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:14624): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:14624): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:14624): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
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

Screen geometry changed:
   0x0x1920x1080

unity-panel-service: no process found
Initializing unityshell options...done
DEBUG 2011-11-20 01:47:23 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1920 h=1080
compiz (core) - Warn: unhandled ConfigureNotify on 0x1c00194!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x1c00194!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x1c00194!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
WARN  2011-11-20 01:47:23 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window60826401: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

Initializing annotate options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing cube options...done
Initializing debugspew options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing mag options...done
Initializing neg options...done
Initializing obs options...done
Initializing opacify options...done
Initializing put options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scaleaddon options...done
Initializing screenshot options...done
Initializing shift options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing thumbnail options...done
Initializing water options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing zoom options...done
Setting Update "main_menu_key"
Setting Update "run_key"
WARN  2011-11-20 01:48:06 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2011-11-20 01:48:06 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2011-11-20 01:48:06 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2011-11-20 01:48:06 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2011-11-20 01:48:10 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method GlobalSearch proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-11-20 01:48:10 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method GlobalSearch proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-11-20 01:48:11 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method GlobalSearch proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-11-20 01:48:11 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method GlobalSearch proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-11-20 01:48:12 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method GlobalSearch proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-11-20 01:48:12 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method GlobalSearch proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-11-20 01:48:19 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method GlobalSearch proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-11-20 01:48:19 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method GlobalSearch proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-11-20 01:48:19 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method GlobalSearch proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-11-20 01:48:19 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method GlobalSearch proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-11-20 01:48:32 unity.glib.dbusproxy GLibDBusProxy.cpp:204 Unable to connect to proxy: Error calling StartServiceByName for com.canonical.Unity.Lens.Applications: Timeout was reached
WARN  2011-11-20 01:48:32 unity.glib.dbusproxy GLibDBusProxy.cpp:204 Unable to connect to proxy: Error calling StartServiceByName for com.canonical.Unity.Lens.Applications: Timeout was reached

---

### Post by nickyspag on 2011-11-20
I am experiencing the similar issue, similar error message as akshay.sulakhe if I  run [FONT="Courier New"]unity --replace[/FONT] in the terminal . The dash shows no applications if i  search or clicking "media apps", "internet apps" or "more apps". Finding/listing files on the other hand works fine.

Note that if I create a new user, and log in as that user, then the dash works fine (I can see applications in different categories as well as applications available to download). This makes me think maybe it's some sort of misconfiguration/old config from previous version? Any idea what config I can clear away? Something in ~/.config or ~/.gconf?

---

### Post by adomenech on 2012-10-22
Try in unity 2D, I remember similar Issue in 12.04 and it was mesa fault. If it works in 2D this is the workarround until an update fixes the 3D

---

