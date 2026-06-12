---
title: "Dash home does not have applications"
date: 2012-09-08
forum: General Help
---

### Post by xcrunner78 on 2012-09-08
Hello,

I am having problems with a recently installed 12.04 OS.  When I go to open an application (i.e., Rhythmbox) from the unity Dash Home, it is not there.  In fact no applications are listed.  I found a solution where in the terminal I enter 

```
unity --reset
```It works until the next time I boot.  In the terminal, this is the what is produced:

```
WARNING: Unity currently default profile, so switching to metacity while resetting the values
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1800004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x4000057

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x321e111

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x32000b8

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3e000b1

Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
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

(compiz:2647): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0xc0009f!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000a2!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000a2!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000a5!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000a8!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000a8!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000ab!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
WARN  2012-09-08 15:47:38 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-09-08 15:47:38 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-09-08 15:47:38 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-09-08 15:47:39 unity <unknown>:0 Failed to fetch type: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window65011889
Initializing staticswitcher options...done
ERROR 2012-09-08 15:47:41 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key"
```
After which it does nothing else and does not give me a command line to enter anything else.  I have been working on solving this problem for the past couple of day with no resolve.  Any help would be greatly appreciated!

Thanks,
Jason

---

### Post by colin.p on 2012-09-08
Is this a new fresh install, or an upgrade over an earlier ubuntu?
If it's an upgrade over a pre-existing install, especially if you have a separate home partition, you may need to remove all your hidden folders in "home" (after making sure you back them all up first). Also any previous PPA's, for that previous version of ubuntu, that could cause you no end of grief (I learned the hard way).

If it's a new fresh install onto a shiny new virgin hard drive, I have no clue.

---

### Post by xcrunner78 on 2012-09-08
Yes, this is a fresh install from a thumb drive.  I also have other problems that I am dealing with that I'll do separate posts on.

I tried the upgrade first, but right after it updated all of the ppa's, the upgrade quit.  I tried to -f install, but that got me nowhere. So I wiped the the hard-drive and re-installed.

Thanks for trying to help!

Jason

---

### Post by xcrunner78 on 2012-09-13
Bump ... this happens sometimes when I boot up and sometimes everything displays in dash home when I boot.

---

### Post by r12van on 2012-10-18
newbie here... bump for the solution.. I have this trouble too.. :(

---

