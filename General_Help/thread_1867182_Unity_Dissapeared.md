---
title: "Unity Dissapeared"
date: 2011-10-22
forum: General Help
---

### Post by benplanet on 2011-10-22
I was setting up some Compiz settings with CCM, specifically the "Scale" plugin with a hot corner and all of a suddent Unity crashes. I restart the computer, and when I log in to the "Ubuntu" session, there is no unity. Just an old a menu on the top bar.  I use the Nvidia-current driver, and amd64 ubuntu - if it helps to know.

I tried removing the compiz settings folder, same thing.

Here is what I get when I do "Unity --replace" or "Unity --reset"

> ben@ben-MS-7640:~$ unity --replace
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
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
Initializing staticswitcher options...[ERROR]: Option "next_button" already defined
[ERROR]: Option "next_key" already defined
[ERROR]: Option "prev_button" already defined
[ERROR]: Option "prev_key" already defined
[ERROR]: Option "next_all_button" already defined
[ERROR]: Option "next_all_key" already defined
[ERROR]: Option "prev_all_button" already defined
[ERROR]: Option "prev_all_key" already defined
[ERROR]: Option "next_group_button" already defined
[ERROR]: Option "next_group_key" already defined
[ERROR]: Option "prev_group_button" already defined
[ERROR]: Option "prev_group_key" already defined
[ERROR]: Option "next_no_popup_button" already defined
[ERROR]: Option "next_no_popup_key" already defined
[ERROR]: Option "prev_no_popup_button" already defined
[ERROR]: Option "prev_no_popup_key" already defined
[ERROR]: Option "next_panel_button" already defined
[ERROR]: Option "next_panel_key" already defined
[ERROR]: Option "prev_panel_button" already defined
[ERROR]: Option "prev_panel_key" already defined
[ERROR]: Option "speed" already defined
[ERROR]: Option "timestep" already defined
[ERROR]: Option "window_match" already defined
[ERROR]: Option "minimized" already defined
[ERROR]: Option "auto_change_vp" already defined
[ERROR]: Option "popup_delay" already defined
[ERROR]: Option "mouse_select" already defined
[ERROR]: Option "saturation" already defined
[ERROR]: Option "brightness" already defined
[ERROR]: Option "opacity" already defined
[ERROR]: Option "icon" already defined
[ERROR]: Option "icon_only" already defined
[ERROR]: Option "mipmap" already defined
[ERROR]: Option "row_align" already defined
[ERROR]: Option "focus_on_switch" already defined
[ERROR]: Option "bring_to_front" already defined
[ERROR]: Option "highlight_mode" already defined
[ERROR]: Option "highlight_rect_hidden" already defined
[ERROR]: Option "highlight_color" already defined
[ERROR]: Option "highlight_border_color" already defined
[ERROR]: Option "highlight_border_inlay_color" already defined
done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done
Starting unity-window-decorator

(unity-window-decorator:22387): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(unity-window-decorator:22387): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(unity-window-decorator:22387): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(unity-window-decorator:22387): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x22000e9



It's worth mentioning that this error caused me to reinstall (fresh install) because I thought something was broken. Unfortunately, this looks like a bug that caused unity to break. and Ubuntu session to have no Unity.

Thanks for the help, I am using Gnome-shell for the time being.

---

### Post by benplanet on 2011-10-22
Solved my own issue. Basically you either need to boot safe mode session or install unity-2d or gnome-shell. login, and go to Advanced Settings Manager for Compiz and re-enable Unity (and fix the conflicts, if any) - now you can successfully boot into the regular ubuntu session with Unity 3D. 

So basically, it had nothing to do with any drivers.. compiz crashed, and disable the Unity plugin (I think it's still a bug, the fact that it crashed)

---

