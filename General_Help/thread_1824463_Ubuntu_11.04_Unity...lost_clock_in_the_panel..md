---
title: "Ubuntu 11.04 Unity...lost clock in the panel."
date: 2011-08-13
forum: General Help
---

### Post by hurryon on 2011-08-13
Somehow I lost the clock in the panel; maybe I uninstalled some packages related to the clock.

Anyone know which package I should install?

Thanks!

---

### Post by Primefalcon on 2011-08-13
> **hurryon said:**
> Somehow I lost the clock in the panel; maybe I uninstalled some packages related to the clock.

Anyone know which package I should install?

Thanks!
it miht not be broken have you tried rebooting or doing a ```
unity --replace
```

---

### Post by flipper T on 2011-08-13
go to time & date settings & make sure "show clock" is ticked

---

### Post by garvinrick4 on 2011-08-13
```
aptitude show unity
```Above will give you what unity package is and tell you what indicators there
are such as your date time indicator.
Pick out which one that is not installed and install it:
sudo apt-get install "package name"
Below is example I am in 11.10 not 11.04 so might look a little different.
```
rick@rick-alpha2:~$ aptitude show unity
Package: unity                           
New: yes
State: installed
Automatically installed: no
Version: 4.8.0-0ubuntu1
Priority: optional
Section: gnome
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 2,408 k
Depends: libatk1.0-0 (>= 1.12.4), libbamf3-0 (>= 0.2.60), libc6 (>= 2.4),
         libcairo2 (>= 1.2.4), libdbus-glib-1-2 (>= 0.78), libdbusmenu-glib4 (>=
         0.4.2), libdee-1.0-1 (>= 0.5.2), libgcc1 (>= 1:4.1.1), libgconf2-4 (>=
         2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libgl1-mesa-glx | libgl1,
         libglew1.5 (>= 1.5.7.is.1.5.2), libglib2.0-0 (>= 2.29.14),
         libgnome-desktop-3-2 (>= 2.91.5), libgtk-3-0 (>= 3.1.6),
         libindicator3-6, libjson-glib-1.0-0 (>= 0.12.0), libnotify4 (>= 0.7.0),
         libnux-1.0-0 (>= 1.2.0), libnux-1.0-0 (< 1.2.2), libpango1.0-0 (>=
         1.20.0), libsigc++-2.0-0c2a (>= 2.0.2), libstartup-notification0 (>=
         0.2), libstdc++6 (>= 4.6), libunity-core-4.0-4 (>= 4.8.0),
         libunity-core-4.0-4 (< 4.10.0), libunity-misc4 (>= 4.0.4),
         libutouch-geis1 (>= 1.0.8), libx11-6, unity-common (= 4.8.0-0ubuntu1),
         compiz, compiz-core, compiz-core-abiversion-20110703,
         compiz-plugins-main-default, libglib2.0-bin, python, nux-tools,
         unity-asset-pool (>= 0.8.18)
[COLOR=Red]Recommends: unity-lens-applications, unity-lens-files, unity-lens-music,
            indicator-appmenu, indicator-application, indicator-sound,
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

rick@rick-alpha2:~$ 

```#If you need aptitude install it:
```
sudo apt-get install aptitude
```You can use this method for lots of issues.
#Also you can run this below and will make you a nice list of installed packages.
Will be in /home.
```
sudo dpkg --get-selections > installedsoftware
```Nice to have true names of packages handy sometimes.

---

### Post by Ildanach on 2011-08-23
having the same problem, solutions didn't solve it though. Any other suggestions?

---

### Post by Pengwyn44 on 2011-08-29
I had the same problem but did not see the posted solution in time and therefore did not try it. As I clone my hard drive every week or so with Clonezilla onto an external drive, I restored the image and replaced any files that had changed since the clone was made. The Home files I back up separately every day and the vital ones go to the Ubuntu cloud.
To anyone whose files are precious I recommend the use of Clonezilla.

Also I've stopped using Unity and have opted for the old style screen.

P.S. Clonezilla works perfectly with that OTHER Operating system!

---

