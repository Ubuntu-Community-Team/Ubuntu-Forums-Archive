---
title: "Time/Date not showing up (11.10)"
date: 2011-10-18
forum: General Help
---

### Post by pimentel28 on 2011-10-18
With Unity (11.10 Oneiric Ocelot), the time/calendar does not show up, even with Evolution installed. I am able to view the time/date with gnome-shell, but with Unity, I can't.

For now, I'm using Gnome shell and KDE until I can get the time/calender to work on Unity :( 

Thanks in advance!

---

### Post by pimentel28 on 2011-10-19
Any help on this would be appreciated :)

---

### Post by mc4man on 2011-10-19
the 1st.thing to check is if indicator-datetime is installed
```
sudo apt-get install indicator-datetime
```

---

### Post by garvinrick4 on 2011-10-19
Below in Red is your indicators in Unity.
```
Package: unity                           
New: yes
State: installed
Automatically installed: no
Version: 4.22.0-0ubuntu3
Priority: optional
Section: gnome
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 2,679 k
Depends: libatk1.0-0 (>= 1.12.4), libbamf3-0 (>= 0.2.60), libc6 (>= 2.4),
         libcairo2 (>= 1.2.4), libdbus-glib-1-2 (>= 0.78), libdbusmenu-glib4 (>=
         0.4.2), libdee-1.0-1 (>= 0.5.12), libgcc1 (>= 1:4.1.1), libgconf2-4 (>=
         2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libgl1-mesa-glx | libgl1,
         libglew1.5 (>= 1.5.7.is.1.5.2), libglib2.0-0 (>= 2.29.14),
         libgnome-desktop-3-2 (>= 2.91.5), libgtk-3-0 (>= 3.1.6),
         libindicator3-6, libjson-glib-1.0-0 (>= 0.12.0), libnotify4 (>= 0.7.0),
         libnux-1.0-0 (>= 1.8.0-0), libpango1.0-0 (>= 1.20.0),
         libsigc++-2.0-0c2a (>= 2.0.2), libstartup-notification0 (>= 0.2),
         libstdc++6 (>= 4.6), libunity-core-4.0-4 (>= 4.14.2), libunity-misc4
         (>= 4.0.4), libutouch-geis1 (>= 1.0.8), libx11-6, libxext6,
         unity-common (= 4.22.0-0ubuntu3), compiz, compiz-core,
         compiz-core-abiversion-20110828, compiz-plugins-main-default,
         libglib2.0-bin, python, nux-tools, unity-asset-pool (>= 0.8.18)
Recommends: unity-lens-applications, unity-lens-files, unity-lens-music,
         [COLOR=Red]   indicator-appmenu, indicator-application, indicator-sound,
            indicator-datetime, indicator-messages, indicator-power,
            indicator-session[/COLOR]
Conflicts: netbook-launcher (< 1:2.1.18-0ubuntu2), netbook-launcher (<
           1:2.1.18-0ubuntu2), unity
Breaks: bamf (< 0.2.76), bamf (< 0.2.76), compiz-core (<
        1:0.9.4+bzr20110606-0ubuntu5), compiz-core (<
        1:0.9.4+bzr20110606-0ubuntu5)
Replaces: netbook-launcher (< 1:2.1.18-0ubuntu2), netbook-launcher (<
          1:2.1.18-0ubuntu2), unity-common (< 4.0.1-0ubuntu2~), unity-common (<
          4.0.1-0ubuntu2~)
Provides: indicator-renderer, netbook-launcher
Description: Interface designed for efficiency of space and interaction.
 Unity is a desktop experience that sings. Designed by Canonical and the Ayatana
 community, Unity is all about the combination of familiarity and the future. We
 bring together visual design, analysis of user experience testing, modern
 graphics technologies and a deep understanding of the free software landscape
 to produce what we hope will be the lightest, most elegant and most delightful
 way to use your PC.
Homepage: https://launchpad.net/unity

rick@rick-test:~$ 

```

---

### Post by Meelad on 2011-10-19
System Settings => Time & Date => Clock => Check if the first Check (Show a clock in the menu bar) is ticked.

---

### Post by pimentel28 on 2011-10-19
> **garvinrick4 said:**
> Below in Red is your indicators in Unity.
```
Package: unity                           
New: yes
State: installed
Automatically installed: no
Version: 4.22.0-0ubuntu3
Priority: optional
Section: gnome
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 2,679 k
Depends: libatk1.0-0 (>= 1.12.4), libbamf3-0 (>= 0.2.60), libc6 (>= 2.4),
         libcairo2 (>= 1.2.4), libdbus-glib-1-2 (>= 0.78), libdbusmenu-glib4 (>=
         0.4.2), libdee-1.0-1 (>= 0.5.12), libgcc1 (>= 1:4.1.1), libgconf2-4 (>=
         2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libgl1-mesa-glx | libgl1,
         libglew1.5 (>= 1.5.7.is.1.5.2), libglib2.0-0 (>= 2.29.14),
         libgnome-desktop-3-2 (>= 2.91.5), libgtk-3-0 (>= 3.1.6),
         libindicator3-6, libjson-glib-1.0-0 (>= 0.12.0), libnotify4 (>= 0.7.0),
         libnux-1.0-0 (>= 1.8.0-0), libpango1.0-0 (>= 1.20.0),
         libsigc++-2.0-0c2a (>= 2.0.2), libstartup-notification0 (>= 0.2),
         libstdc++6 (>= 4.6), libunity-core-4.0-4 (>= 4.14.2), libunity-misc4
         (>= 4.0.4), libutouch-geis1 (>= 1.0.8), libx11-6, libxext6,
         unity-common (= 4.22.0-0ubuntu3), compiz, compiz-core,
         compiz-core-abiversion-20110828, compiz-plugins-main-default,
         libglib2.0-bin, python, nux-tools, unity-asset-pool (>= 0.8.18)
Recommends: unity-lens-applications, unity-lens-files, unity-lens-music,
         [COLOR=Red]   indicator-appmenu, indicator-application, indicator-sound,
            indicator-datetime, indicator-messages, indicator-power,
            indicator-session[/COLOR]
Conflicts: netbook-launcher (< 1:2.1.18-0ubuntu2), netbook-launcher (<
           1:2.1.18-0ubuntu2), unity
Breaks: bamf (< 0.2.76), bamf (< 0.2.76), compiz-core (<
        1:0.9.4+bzr20110606-0ubuntu5), compiz-core (<
        1:0.9.4+bzr20110606-0ubuntu5)
Replaces: netbook-launcher (< 1:2.1.18-0ubuntu2), netbook-launcher (<
          1:2.1.18-0ubuntu2), unity-common (< 4.0.1-0ubuntu2~), unity-common (<
          4.0.1-0ubuntu2~)
Provides: indicator-renderer, netbook-launcher
Description: Interface designed for efficiency of space and interaction.
 Unity is a desktop experience that sings. Designed by Canonical and the Ayatana
 community, Unity is all about the combination of familiarity and the future. We
 bring together visual design, analysis of user experience testing, modern
 graphics technologies and a deep understanding of the free software landscape
 to produce what we hope will be the lightest, most elegant and most delightful
 way to use your PC.
Homepage: https://launchpad.net/unity

rick@rick-test:~$ 

```

Thanks, this worked :) 

Also, a fresh install of Oneiric already had the clock showing up.

---

