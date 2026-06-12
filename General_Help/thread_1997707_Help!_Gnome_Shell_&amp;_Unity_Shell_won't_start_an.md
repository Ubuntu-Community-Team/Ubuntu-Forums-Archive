---
title: "Help! Gnome Shell &amp; Unity Shell won't start anymore"
date: 2012-06-05
forum: General Help
---

### Post by WG- on 2012-06-05
Help! Since 12.04 I often got a error dialog, in which you are requested to send data to the ubuntu developers so they could solve the problem. Before 12.04 I never used to get those messages. 

The errors that occured which the dialog said never lead to a problem. It was always "oh error, *click*click* continue. They were always very vague.

Now I just started up my laptop and wanted to login into GNOME3.4 and then the laptop does nothing, it seems to loads everything accept the GNOME shell. So what I end up is, is my default wallpaper. I can then do ctrl+alt+delete to logout. The same is for Unity. 

Anyone can help me solve this problem? I do not want to reinstall everything :-(

Laptop: Toshiba Portegé M750
OS: Ubuntu 12.04
Shell: GNOME 3.4

ps. now I am on GNOME classic and everything works fine.

---

### Post by WG- on 2012-06-06
Anyone?

---

### Post by dino99 on 2012-06-06
boot in recovery mode to:

- check errors and update packages
- open a root session to:
clean the system
      ```
apt-get clean
      apt-get autoclean
      apt-get autoremove
      apt-get update
      apt-get install -f
      apt-get install --reinstall ubuntu-desktop
      dpkg-reconfigure -a
```

then reboot and open a user session to check if the problems are gone. If not, then redo the previous step by opening a root session from recovery mode and:
```
apt-get purge unity*
apt-get purge gnome-shell
apt-get install unity
apt-get install unity-2d
apt-get install gnome-shell
dpkg-reconfigure -a

```

note: if you got these issues after installation bleeding edge packages from ppas, then purge these ppas with purge-ppa

---

### Post by WG- on 2012-06-07
Question how would you have me do that in recovery mode? I don't got internet connection then. And when I select in the recovery menu to make network connection it boots and I get the normal ubuntu session. For some reason I don't have a netroot option. 

Photo of recovery mode: [https://docs.google.com/file/d/0B_bYHK2zQCWETzR4anpwX3hwbUE/edit](https://docs.google.com/file/d/0B_bYHK2zQCWETzR4anpwX3hwbUE/edit)

---

### Post by philinux on 2012-06-07
> **WG- said:**
> Help! Since 12.04 I often got a error dialog, in which you are requested to send data to the ubuntu developers so they could solve the problem. Before 12.04 I never used to get those messages. 

The errors that occured which the dialog said never lead to a problem. It was always "oh error, *click*click* continue. They were always very vague.

Now I just started up my laptop and wanted to login into GNOME3.4 and then the laptop does nothing, it seems to loads everything accept the GNOME shell. So what I end up is, is my default wallpaper. I can then do ctrl+alt+delete to logout. The same is for Unity. 

Anyone can help me solve this problem? I do not want to reinstall everything :-(

Laptop: Toshiba Portegé M750
OS: Ubuntu 12.04
Shell: GNOME 3.4

ps. now I am on GNOME classic and everything works fine.

Log into a unity session. ctrl alt t to get a terminal and use ```
unity --reset
```

---

### Post by WG- on 2012-06-08
> **philinux said:**
> Log into a unity session. ctrl alt t to get a terminal and use ```
unity --reset
```

I don't know but it seems the command does not finish... It starts running and then after a while it will only output 

"Compiz (opengl) - Fatal: Root visual is not a GL visual" 

every 1-2 minuts.

log:
```
unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
Window manager warning: GConf key '/apps/metacity/general/action_double_click_titlebar' is set to an invalid value

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:16007): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1c00004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1800002

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1a00002

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x24006b1

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2628ff5

Initializing composite options...done
Compiz (opengl) - Fatal: Root visual is not a GL visual
compiz (opengl) - Error: initScreen failed
compiz (core) - Error: Couldn't activate plugin 'opengl'
compiz (core) - Error: Plugin 'opengl' not loaded.

Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Compiz (opengl) - Fatal: Root visual is not a GL visual
Initializing resize options...done
Initializing place options...done
Initializing move options...done
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: InitPlugin 'wall' failed
compiz (core) - Error: Couldn't activate plugin 'wall'
Compiz (opengl) - Fatal: Root visual is not a GL visual
Initializing grid options...done
Initializing session options...done
Initializing gnomecompat options...done
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: InitPlugin 'animation' failed
compiz (core) - Error: Couldn't activate plugin 'animation'
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: InitPlugin 'fade' failed
compiz (core) - Error: Couldn't activate plugin 'fade'
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: InitPlugin 'unitymtgrabhandles' failed
compiz (core) - Error: Couldn't activate plugin 'unitymtgrabhandles'
compiz (core) - Error: Plugin 'opengl' not loaded.

Compiz (opengl) - Fatal: Root visual is not a GL visual
Initializing workarounds options...done
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: InitPlugin 'scale' failed
compiz (core) - Error: Couldn't activate plugin 'scale'
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: InitPlugin 'expo' failed
compiz (core) - Error: Couldn't activate plugin 'expo'
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: InitPlugin 'ezoom' failed
compiz (core) - Error: Couldn't activate plugin 'ezoom'
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: InitPlugin 'unityshell' failed
compiz (core) - Error: Couldn't activate plugin 'unityshell'
Compiz (opengl) - Fatal: Root visual is not a GL visual
compiz (core) - Warn: unhandled ConfigureNotify on 0xe00090!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xe00093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xe00096!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xe0009c!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xe0009f!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xe0009f!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Initializing animation options...done
Initializing expo options...done
Initializing ezoom options...done
Initializing fade options...done
Initializing opengl options...done
Initializing scale options...done
Initializing staticswitcher options...done
Initializing unitymtgrabhandles options...done
Initializing unityshell options...done
Initializing wall options...done
Setting Update "main_menu_key"
Setting Update "run_key"
Starting gtk-window-decorator
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2628ff5

Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (opengl) - Fatal: Root visual is not a GL visual

```

---

