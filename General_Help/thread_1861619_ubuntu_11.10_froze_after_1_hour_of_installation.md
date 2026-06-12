---
title: "ubuntu 11.10 froze after 1 hour of installation"
date: 2011-10-15
forum: General Help
---

### Post by Amgad elsaiegh on 2011-10-15
after a fresh install of 11.10 & installing all updates and drivers, i wanted to make some tweaks to unity so i installed compiz , once i opened it the system freezed for 2 seconds then compiz crashed ,  lost unity and the top panel , i tried to show them using keyboard shortcuts but failed ,reset my pc but after login, same problem exists, tried unity 2d, gnome shell with no use, all of them have no panels and no keyboard shortcuts are working ,the screen makes weird flicks  it seems to be a conflict in display drivers [i have frglx installed] , any solutions guys???


i am to depressed :( ,  writing this thread from windows 7 now

---

### Post by smurf69 on 2011-10-15
Had the same issue as well.I reinstalled ubuntu and everything is perfect :S but i guess is not the best solution :)

---

### Post by watgrad on 2011-10-15
I had this problem too...
What worked for me - not saying you should do this, but I got things working well this way...

Ctrl - Alt - T for a terminal

unity --reset

reboot computer

I then opened Software Sources and enabled "Pre-release updates" and "unsupported updates" in the Updates panel. Then ran update manager - new versions of compiz were installed which seem to have solved the problem.

---

### Post by Amgad elsaiegh on 2011-10-16
i tried unity ---reset and it failed too :confused: , here is what came up

> unity-panel-service: no process found
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

(unity-window-decorator:1726): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(unity-window-decorator:1726): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(unity-window-decorator:1726): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(unity-window-decorator:1726): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",




anything useful guys ?

---

### Post by Amgad elsaiegh on 2011-10-17
no answer yet ?

---

