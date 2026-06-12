---
title: "Alt-Tab to switch windows crashes"
date: 2012-04-15
forum: General Help
---

### Post by drusmanbashir on 2012-04-15
Hi , I have recently installed ubuntu 11.10 on my HP laptop .. my desktop freezes 60% of the times i try alt-tab to switch windows. i installed compiz but the problem persists with that too. i am copy-pasting a log from compiz

sman@Dorothy:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
usman@Dorothy:~$ compiz --replace
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
Initializing resize options...done
Initializing wall options...done
Initializing gnomecompat options...done
Initializing place options...done
Initializing session options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing grid options...done
Initializing move options...done
Initializing fade options...done
Initializing workarounds options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing scale options...done
Initializing ezoom options...done
Initializing unitymtgrabhandles options...done

Screen geometry changed:
   0x0x1366x768

Initializing unityshell options...done
Initializing switcher options...done
DEBUG 2012-04-15 12:09:42 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1366 h=768
Setting Update "main_menu_key"
Setting Update "run_key"
Setting Update "alt_tab_prev"
WARN  2012-04-15 12:10:27 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-04-15 12:10:27 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-04-15 12:10:27 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-04-15 12:10:27 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-04-15 12:10:27 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2012-04-15 12:10:27 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2012-04-15 12:10:27 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2012-04-15 12:10:27 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2012-04-15 12:10:29 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2012-04-15 12:10:29 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory
WARN  2012-04-15 12:10:44 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window65011842: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2012-04-15 12:10:44 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window65011842: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2012-04-15 12:10:44 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-04-15 12:10:45 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-04-15 12:10:45 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-04-15 12:10:45 glib.glib-gobject <unknown>:0 invalid unclassed pointer in cast to `BamfView'
WARN  2012-04-15 12:10:45 glib.glib-gobject <unknown>:0 invalid unclassed pointer in cast to `GObject'
WARN  2012-04-15 12:10:45 glib.glib-gobject <unknown>:0 instance with invalid (NULL) class pointer
WARN  2012-04-15 12:10:45 glib.glib-gobject <unknown>:0 instance with invalid (NULL) class pointer
WARN  2012-04-15 12:10:45 glib.glib-gobject <unknown>:0 instance with invalid (NULL) class pointer
WARN  2012-04-15 12:10:45 glib.glib-gobject <unknown>:0 instance with invalid (NULL) class pointer
WARN  2012-04-15 12:10:45 glib.glib-gobject <unknown>:0 instance with invalid (NULL) class pointer
WARN  2012-04-15 12:10:45 glib.glib-gobject <unknown>:0 instance with invalid (NULL) class pointer
WARN  2012-04-15 12:10:45 glib.glib-gobject <unknown>:0 instance with invalid (NULL) class pointer
Segmentation fault


the segmentation fault at the end seems to have happened when i pressed alt-tab a second time and this time the freeze-up was worse so i had to do a hard-boot. please help

---

