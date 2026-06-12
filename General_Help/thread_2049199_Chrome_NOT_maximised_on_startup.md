---
title: "Chrome NOT maximised on startup"
date: 2012-08-28
forum: General Help
---

### Post by finechap on 2012-08-28
**Every time Chrome is updated**, it reverts to opening small screen [NOT maximised]. This is very **irritating**.

In order to reset it to open **maximised**, you need to change the general command parameter in */usr/share/applications*.
Find the Google Chrome icon [desktop configuration file] and right click (clack).
Select properties, which shows the basic properties. One of these is the command used:-
*/opt/google/chrome/google-chrome %U*
Add ^-start-maximized [^ is a space]. It is now:-
*/opt/google/chrome/google-chrome %U -start-maximized *

If you have root permission while doing this, it is now fixed, until the next update of Chrome. If not then the change will not happen.
You will have to visit this page, in order to install root file browsing, using "gksudo nautilus":-
[http://ubuntuforums.org/showthread.php?t=1685916]("http://ubuntuforums.org/showthread.php?t=1685916")

That's better \\:D/
Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-29-generic
GNOME 3.4.2

---

