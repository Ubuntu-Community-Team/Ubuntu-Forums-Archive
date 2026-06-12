---
title: "Unity Launcher Problem"
date: 2011-11-10
forum: General Help
---

### Post by Bosnic on 2011-11-10
I don't know what I did, but I can't see Unity launcher anymore. I can only get it when I log into Ubuntu with "Ubuntu 2D" selected. It might have something to do with me installing CompizConfig Settings Manager.

When I do "sudo unity" I get this:

> compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2c000db

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2000191

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x200019f

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2c000db
EDIT: Just tried uninstaling CCSM. Didn't work. I also uninstalled Unity and then reinstalled it, also didn't work.

And when I do "sudo unity --reset" I get this:

> WARNING: no current gconf profile set, assuming unity
WARNING: Unity currently default profile, so switching to metacity while resetting the values

(metacity:3107): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
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
compiz (core) - Warn: no exact match for ConfigureNotify on 0x3200092!
compiz (core) - Warn: expected the following changes:
compiz (core) - Warn: sibling: 0x9670450
compiz (core) - Warn: instead got:
compiz (core) - Warn: x: 0
compiz (core) - Warn: y: 0
compiz (core) - Warn: width: 1440
compiz (core) - Warn: height: 900
compiz (core) - Warn: above: 0
compiz (core) - Warn: this should never happen. you should probably file a bug about this.


---

### Post by Bosnic on 2011-11-10
Resolved.

Used the fix found here: [http://askubuntu.com/questions/76438/need-to-restore-default-11-10-graphics-how-do-i-do-it](http://askubuntu.com/questions/76438/need-to-restore-default-11-10-graphics-how-do-i-do-it)

---

