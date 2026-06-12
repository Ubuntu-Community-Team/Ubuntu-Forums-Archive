---
title: "KeePassX AutoType on 12.04"
date: 2012-05-07
forum: General Help
---

### Post by akgrant on 2012-05-07
Hi All,

When using the AutoType in KeePassX 0.4.3 on Ubuntu 12.04 the KeePassX window is being closed instead of minimised leaving the keepassx process behind but inaccessible.

Downloading and building the source allows the system tray option to be used, but this doesn't help as it doesn't have an option for re-opening the window (and I assume there is a reason it was disabled in the default distribution).

Any suggestions?

Thanks very much,
Alistair

---

### Post by kostkon on 2012-05-07
> **akgrant said:**
> Hi All,

When using the AutoType in KeePassX 0.4.3 on Ubuntu 12.04 the KeePassX window is being closed instead of minimised leaving the keepassx process behind but inaccessible.

Downloading and building the source allows the system tray option to be used, but this doesn't help as it doesn't have an option for re-opening the window (and I assume there is a reason it was disabled in the default distribution).

Any suggestions?

Thanks very much,
Alistair
Wait, wait. Have you checked its settings. Because it has 3 options that control its tray icon and minimise behaviour.

* Show system tray icon
* Minimise to tray instead of taskbar
* Minimise to tray when clicking the main window's close button

If you disable the tray icon, because as you say it lacks the open option (that's because the qt tray icon is being changed to an indicator on-the-fly by [sni-qt]("http://packages.ubuntu.com/precise/sni-qt")), then keepassx will never minise to the tray and thus it won't disappear. If you want to keep the tray icon, try deselecting the 2nd option, if it's already selected. Also, the 3rd option better left deselected, too.

Hope that helps.

---

### Post by akgrant on 2012-05-07
> **kostkon said:**
> Wait, wait. Have you checked its settings. Because it has 3 options that control its tray icon and minimise behaviour.

* Show system tray icon
* Minimise to tray instead of taskbar
* Minimise to tray when clicking the main window's close button

If you disable the tray icon, because as you say it lacks the open option (that's because the qt tray icon is being changed to an indicator on-the-fly by [sni-qt]("http://packages.ubuntu.com/precise/sni-qt")), then keepassx will never minise to the tray and thus it won't disappear. If you want to keep the tray icon, try deselecting the 2nd option, if it's already selected. Also, the 3rd option better left deselected, too.

Hope that helps.

Hi Kostkon,

Thanks very much for your reply.  On my system both version - Ubuntu and compiled - close the window regardless of whether the system tray icon is enabled or not (2nd and 3rd options are also deselected).

The window seems to be in some zombie state as the icon is still present, but attempting to switch to the window just causes the icon to disappear.

Thanks again,
Alistair

---

### Post by akgrant on 2012-05-22
For anyone interested, the issue is now being tracked in launchpad: [https://bugs.launchpad.net/ubuntu/+source/keepassx/+bug/996756](https://bugs.launchpad.net/ubuntu/+source/keepassx/+bug/996756)

---

