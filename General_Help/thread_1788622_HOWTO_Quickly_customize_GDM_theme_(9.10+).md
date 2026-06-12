---
title: "HOWTO: Quickly customize GDM theme (9.10+)"
date: 2011-06-22
forum: General Help
---

### Post by animacide on 2011-06-22
The following trick will let you quickly and easily customize the theme and background used by GDM in Ubuntu 9.10+.

Just fire up your trusty terminal and paste in the following:

```

xhost +; DISPLAY=:0;HOME=/var/lib/gdm/ sudo -u gdm gnome-appearance-properties; xhost -

```

NOTE: While slight, this trick does impose a temporary security flaw.  The 'xhost +' allows anything to connect to your display.  This will revert back to normal at the end with 'xhost -'.  However, while you are configuring GDM your X server will be temporarily insecure, so only do this on a trusted network.

---

