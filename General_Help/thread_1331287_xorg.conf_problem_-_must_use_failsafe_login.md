---
title: "xorg.conf problem - must use failsafe login"
date: 2009-11-19
forum: General Help
---

### Post by Bill magee on 2009-11-19
I have been running Karmic about a week. No problems until today. Cannot login with gnome, must use failsafe gnome. Tried X -configure, no improvement. 

Running an Acer Travelmate with intel gm965.

Here is my .xsession-errors file:

```

Unable to create /home/bill/.dbus/session-bus

(gnome-settings-daemon:2612): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:2612): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_to_workspace_down"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_group"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_panels"
Window manager warning: "" found in configuration database is not a valid value for keybinding "cycle_windows"
Window manager warning: "" found in configuration database is not a valid value for keybinding "cycle_panels"
Window manager warning: "" found in configuration database is not a valid value for keybinding "show_desktop"
Window manager warning: "" found in configuration database is not a valid value for keybinding "panel_main_menu"
Window manager warning: "" found in configuration database is not a valid value for keybinding "panel_run_dialog"
Window manager warning: "" found in configuration database is not a valid value for keybinding "run_command_screenshot"
Window manager warning: "" found in configuration database is not a valid value for keybinding "run_command_window_screenshot"
Window manager warning: "" found in configuration database is not a valid value for keybinding "activate_window_menu"
Window manager warning: "" found in configuration database is not a valid value for keybinding "maximize"
Window manager warning: "" found in configuration database is not a valid value for keybinding "unmaximize"
Window manager warning: "" found in configuration database is not a valid value for keybinding "minimize"
Window manager warning: "" found in configuration database is not a valid value for keybinding "close"
Window manager warning: "" found in configuration database is not a valid value for keybinding "begin_move"
Window manager warning: "" found in configuration database is not a valid value for keybinding "begin_resize"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_left"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_right"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_up"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_down"
Window manager warning: Failed to read saved session file /home/bill/.config/metacity/sessions/10563793a8c42f53212586273771211100000025980001.ms: Failed to open file '/home/bill/.config/metacity/sessions/10563793a8c42f53212586273771211100000025980001.ms': No such file or directory

(nautilus:2652): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** (gnome-panel:2644): DEBUG: Adding applet 0.
** (gnome-panel:2644): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:2644): DEBUG: Adding applet 1.
** (gnome-panel:2644): DEBUG: Adding applet 2.
** (gnome-panel:2644): DEBUG: Adding applet 3.
** (gnome-panel:2644): DEBUG: Adding applet 4.

** (nautilus:2652): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2652): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2652): WARNING **: No marshaller for signature of signal 'ShareCreateError'
** (gnome-panel:2644): DEBUG: Adding applet 5.
** (gnome-panel:2644): DEBUG: Adding applet 6.
** (gnome-panel:2644): DEBUG: Adding applet 7.
** (gnome-panel:2644): DEBUG: Adding applet 8.
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (gnome-panel:2644): DEBUG: Adding applet 9.

```

---

