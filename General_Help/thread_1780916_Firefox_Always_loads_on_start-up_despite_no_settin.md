---
title: "Firefox Always loads on start-up despite no setting for it???"
date: 2011-06-12
forum: General Help
---

### Post by Matt Pellegrini on 2011-06-12
Every time i start Ubuntu, Firefox loads as soon as i log in. I've checked the list of start-up applications and it's not there, the option to automatically remember open applications is unchecked in both startup application settings and Ubuntu tweak. Is there some other place that has this setting or any setting that would cause Firefox to load on boot? Is there a setting in Firefox I'm missing?

Basically how do i stop this from happening?

(I've tried reinstalling and that didn't fix it)

Thanks in advance for any help.

---

### Post by sikander3786 on 2011-06-12
Please post the output of this command.

```
ls -l ~/.config/autostart
```

---

### Post by Matt Pellegrini on 2011-06-12
firefox isn't there,

-rw-r--r-- 1 matt matt 159 2011-06-07 17:53 awn.desktop
-rw-r--r-- 1 matt matt 176 2011-06-11 21:52 docky.desktop
-rw-r--r-- 1 matt matt 329 2011-02-16 09:13 empathy.desktop
-rw-r--r-- 1 matt matt 475 2011-06-11 21:53 evolution-alarm-notify.desktop
-rw-r--r-- 1 matt matt 526 2011-06-11 21:53 gnome-at-session.desktop
-rw-r--r-- 1 matt matt 170 2011-06-08 13:51 Screenlets Daemon.desktop
-rw-r--r-- 1 matt matt 240 2011-06-12 21:16 ubuntuone-launch.desktop

---

### Post by sikander3786 on 2011-06-12
Strange. Just wondering what that 'gnome-at-session.desktop' file contains? Not sure what it is intended for.

```
gedit ~/.config/autostart/gnome-at-session.desktop
```

---

### Post by pqwoerituytrueiwoq on 2011-06-12
> **sikander3786 said:**
> Strange. Just wondering what that 'gnome-at-session.desktop' file contains? Not sure what it is intended for.

```
gedit ~/.config/autostart/gnome-at-session.desktop
```
this is what mine has
```
[Desktop Entry]
Name=Visual Assistance
Comment=Start the preferred visual assistive technology
Exec=gnome-at-visual -s
Icon=preferences-desktop-accessibility
Terminal=false
Type=Application
StartupNotify=false
OnlyShowIn=GNOME;
AutostartCondition=GNOME /desktop/gnome/interface/accessibility
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-control-center
X-GNOME-Bugzilla-Component=other capplets
X-GNOME-Bugzilla-Version=2.30.1
X-GNOME-Autostart-enabled=false
X-Ubuntu-Gettext-Domain=gnome-control-center-2.0
```

---

### Post by Matt Pellegrini on 2011-06-12
[Desktop Entry]
Name=Visual Assistance
Comment=Start the preferred visual assistive technology
Exec=gnome-at-visual -s
Icon=preferences-desktop-accessibility
Terminal=false
Type=Application
StartupNotify=false
OnlyShowIn=GNOME;
AutostartCondition=GNOME /desktop/gnome/interface/accessibility
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-control-center
X-GNOME-Bugzilla-Component=other capplets
X-GNOME-Bugzilla-Version=2.32.0
X-GNOME-Autostart-enabled=false
X-Ubuntu-Gettext-Domain=gnome-control-center-2.0


Seems the same

---

### Post by sikander3786 on 2011-06-12
Thanks **pqwoerituytrueiwoq** for the post. That looks like controlling the accessibility options. Not found on my PC though.

@** Matt Pellegrini**:

You can try a few things. Exit every running application including Firefox and then in Startup Applications, enable the box for "Remember currently running applications". Reboot and see if Firefox still comes up. Don't forget to un-check that box in the next session.

If that doesn't work, try renaming the firefox directory under ~/.mozilla to something else like firefox.old. It would get rid of your bookmarks and preferences but this is just for a test and you can later put that firefox directory back as it was previously.

---

### Post by Matt Pellegrini on 2011-06-12
well clicking remeber currently running programs, with nothing open, worked....

now i'll reboot again...

---

### Post by Matt Pellegrini on 2011-06-12
Great, didn't load up. Thanks for the help sikander. No idea what that was but i'll mark solved in case anyone happens to find themselves in this situation.

---

