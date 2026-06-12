---
title: "gnome-settings-daemon does not work as expected"
date: 2010-10-28
forum: General Help
---

### Post by jancogo on 2010-10-28
I just installed Ubuntu 10.10 on a brand new HP EliteBook 8540w with an Nvidia card. To get the machine to work at all I have to use the proprietary nvidia driver. The downside is that when I use this driver gnome-settings-daemon seems to crash when I start the machine which results in a ugly theme. To fix this I have to run the following command:

```
sudo gnome-settings-daemon
```

After this the theme is re-applied. If I try to run gnome-settings-daemon as my regular user I get the following messages:

```
** (gnome-settings-daemon:2187): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:2187): WARNING **: Could not acquire name
```

When run as root it works, but I get these messages:

```
** (gnome-settings-daemon:2215): WARNING **: Grab failed for some keys, another application may already have access the them.

** (gnome-settings-daemon:2215): WARNING **: Clipboard manager is already running.
```

Anyone else who has this problem? If not, could someone help me debug this problem?

---

### Post by jancogo on 2011-02-04
Bump.

Still not fixed. Am I the only one who has this problem? Could someone help me debug this problem?

---

