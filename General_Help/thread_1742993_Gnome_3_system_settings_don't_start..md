---
title: "Gnome 3 system settings don't start."
date: 2011-04-29
forum: General Help
---

### Post by folone on 2011-04-29
When I try to launch gnome system settings, I get segfault:

```
georgii@gleontiev:~$ gnome-settings-daemon

** (gnome-settings-daemon:2599): WARNING **: Ignoring unknown module 'org.gnome.settings-daemon.plugins.gconf'

** (gnome-settings-daemon:2599): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:2599): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.

** (gnome-settings-daemon:2599): WARNING **: Name taken or bus went away - shutting down
Segmentation fault
```

What is wrong here?

---

### Post by folone on 2011-04-29
I tried this: [http://ubuntuforums.org/showpost.php?p=3776732&postcount=15](http://ubuntuforums.org/showpost.php?p=3776732&postcount=15) , and restarted dbus after with ```
sudo /etc/init.d/dbus restart
``` and rebooting.

Now it says:

```
** (gnome-settings-daemon:2191): WARNING **: Ignoring unknown module 'org.gnome.settings-daemon.plugins.gconf'

** (gnome-settings-daemon:2191): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:2191): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.
[1304083320,000,xklavier.c:xkl_engine_start_listen/] 	The backend does not require manual layout management - but it is provided by the application

(gnome-settings-daemon:2191): media-keys-plugin-WARNING **: Grab failed for some keys, another application may already have access the them.

(gnome-settings-daemon:2191): clipboard-plugin-WARNING **: Clipboard manager is already running.

** (gnome-settings-daemon:2191): WARNING **: Name taken or bus went away - shutting down
Segmentation fault
```

I am probably running another settings manager. The question is how do I stop it?

---

### Post by folone on 2011-04-29
Succesfully started it with ```
gnome-control-center
```
But it does not seem to change anything. For example, it does not change my keyboard layouts and shortcuts to change them.

---

### Post by folone on 2011-04-29
Probably, gnome-control-center is a frontend for gconf-editor, and gnome3 uses settings from dconf-editor. I opened it, and yes, there are no settings for keyboard layouts there. But when I tried to add some (like layouts -> [us,ru] instead of []), it won't let me: Error setting value: 1-3:unknown keyword.

How do I add my layouts there? Is there any frontend for dconf-editor?

---

### Post by Grumbel on 2011-04-29
Can't provide a solution, but I can confirm the problem:

```

$ gnome-settings-daemon 

** (gnome-settings-daemon:4089): WARNING **: Ignoring unknown module 'org.gnome.settings-daemon.plugins.gconf'

** (gnome-settings-daemon:4089): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:4089): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.

(gnome-settings-daemon:4089): keybindings-plugin-WARNING **: Key binding (screenreader) is incomplete

** (gnome-settings-daemon:4089): WARNING **: Name taken or bus went away - shutting down
Segmentation fault

```

This happens when running in Gnome2, but with Gnome3 installed on the system, maybe a conflict between the two or something like that.

Edit: Correction, gnome-setting-daemon actually launches at login, but it simply work, changes of the UI theme for example aren't communicated to all Gnome apps.

---

### Post by supr0 on 2011-05-04
I confirm this problem. Is there a work-around for this?

---

### Post by mockdeep on 2011-10-01
Same problem here.  Have any of you managed to work around this?  When I click on System Settings in the Applications area I get an error, nothing happens when I click on it in the user menu.  gnome-control-center pops up with an empty window.

---

### Post by yellowtrolley on 2011-10-10
I am on Archlinux x64. Having the same problem. 
After an update 'system settings' from the menu was not working anymore. No wonder why! gnome-control-center package was not installed!!! Htf it got removed I don't know but after installing it is back again working.

---

