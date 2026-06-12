---
title: "How can you know which command runs when you change something in a GUI menu?"
date: 2011-05-13
forum: General Help
---

### Post by vezolmi on 2011-05-13
I explain in with an example:

Imagine you want to know which command is carried out when, after executing gnome-mouse-properties, you go to the Touchpad tab and click on "Enable mouse clicks with touchpad".

Another example:

Imagine you want to know the command that is executed when, after running gnome-appearance-properties, you go to the "Visual Effects" tab and click on None.

I've had a look via gnome-system-log in all the log files of the left with no success. Perhaps the commands that run when one changes things in the GUI menus are logged in some other file. Or perhaps they are not stored in any log. In this case there is probably some terminal command to know it, or some program for this.

I think that know that no xorg.conf is used by default this is something to have into account.

Any information is welcome. Thanks.

---

### Post by amauk on 2011-05-13
The GUI doesn't typically "run" external commands

When you change a setting via the GUI, your system will be changed in some way, but that change was done by the GUI program not any other external program

To use your examples
> after executing gnome-mouse-properties, you go to the Touchpad tab and click on "Enable mouse clicks with touchpad".No separate external command is executed when checking "Enable mouse clicks with touchpad", the GUI program itself changes the setting

The setting is in gconf (it's a central database of settings, similar to the windows registry)

Run "gconf-editor", and navigate to
apps > desktop > gnome > peripherals > touchpad
The particular option is "tap_to_click"

---

### Post by vezolmi on 2011-05-22
Thanks.

For the example of gnome-mouse-properties I've verified that the stated change in that GUI menu changes a setting or value in Gconf, as you explain. NB: The Key name is /desktop/gnome/peripherals/touchpad/tap_to_click , without apps in the beginning.

But for the example of gnome-appearance-properties when the stated change in that GUI menu takes place no change seems to happen in Gconf (for example /desktop/gnome/applications/window_manager/current remains as /usr/bin/compiz when Metacity replaces Compiz). It seems to happen the same that when running this command:
```
metacity --replace
``` (it can be done from the Run dialog (ALT+F2)).

(more info in [http://ubuntuforums.org/showthread.php?t=772503](http://ubuntuforums.org/showthread.php?t=772503))

Anybody knows a general method to find any change done via any GUI menu, including those that change something in Gconf and those that not (change something else)?

Thanks

---

### Post by vezolmi on 2011-05-26
I've installed and tried gnome-activity-journal (Zeitgeist) but it's not for this (yes for files, but not for applications).

---

