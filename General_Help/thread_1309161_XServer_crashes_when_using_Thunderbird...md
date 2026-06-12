---
title: "XServer crashes when using Thunderbird.."
date: 2009-11-01
forum: General Help
---

### Post by joto75 on 2009-11-01
Im throwed to login screen while using thunderbird. More messages there are on the folder, more likely this crash will happen (longer it loads, more likely it will crash).. 

Hey, im not too experienced with Ubuntu but this is what i have done
1) have removed all addons
2) Have used thunderbird -safe-mode
3) did apt-get remove thunderbird / apt-get install thunderbird

Ubuntu 9.04
Gnome 2.26.1
Thunderbird: 2.0.0.23

syslog:
Nov  1 12:09:37 peruna x-session-manager[6448]: WARNING: Detected that screensaver has left the bus 
Nov  1 12:09:37 peruna gdm[6359]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov  1 12:09:38 peruna console-kit-daemon[2399]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(
null)' 
Nov  1 12:09:38 peruna console-kit-daemon[2399]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK
_INSTANCE (instance)' failed 


No help. Crash happens. What could i do?

Thanks,
Joni

---

