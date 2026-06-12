---
title: "Is there a way to show gnome daemon my edid"
date: 2012-09-04
forum: General Help
---

### Post by red13 on 2012-09-04
I have a few errors in my xsession but I want to go one at a time. I will give the whole error list incase its relevant.

(gnome-settings-daemon:1867): color-plugin-WARNING **: failed to get edid: unable to get EDID for output
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done

(gnome-settings-daemon:1867): color-plugin-WARNING **: unable to get EDID for xrandr-default: unable to get EDID for output

(gnome-settings-daemon:1867): color-plugin-WARNING **: failed to reset xrandr-default gamma tables: gamma size is zero
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
** Message: applet now removed from the notification area
Initializing move options...done
Initializing wall options...done
** Message: using fallback from indicator to GtkStatusIcon
Initializing grid options...done
I/O warning : failed to load external entity "/home/james/.compiz/session/108aa568705fd059a6134659718463564600000018190034"
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:1886): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
Initializing staticswitcher options...done
Setting Update "icon_size"
Setting Update "main_menu_key"
Setting Update "run_key"
** Message: moving back from GtkStatusIcon to indicator
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (zeitgeist-datahub:2163): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!

I can get the ided from nvidia-settings, is there a way to place it somewhere that then gnome could see it?

---

