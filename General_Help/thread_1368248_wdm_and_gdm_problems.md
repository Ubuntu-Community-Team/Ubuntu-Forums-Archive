---
title: "wdm and gdm problems"
date: 2009-12-30
forum: General Help
---

### Post by raphaelmsx on 2009-12-30
I am having problems with wdm and gdm.

I've just installed Ubuntu 9.10 from the mini iso, then installed wdm and gdm as the login managers, and the following wm/de: xfwm, xfce, twm, vtwm, icewm, fluxbox and afterstep.

When using wdm the following does not appear on the menu list: afterstep and fluxbox.... and when using gdm, xfwm and vtwm does not appear.

Also, xfwm is not working, after wdm validates the user, it simply blanks the screen with a working mouse pointer...

How can I fix all of that?

Thank you.

---

### Post by Brandon Williams on 2009-12-30
I don't know anything about wdm or where it gets its session list from. gdm gets its sessions list from the .desktop files in /usr/share/xsessions/. Adding new .desktop files there will add new session types to the gdm menu.

I also don't know anything about vtwm. To get a fully functioning xfce environment, you probably want to install xfce4, which depends upon all of the various important elements of the environment. Among other things, this includes xfce4-utils, which will install xfce4.desktop in /usr/share/xsessions/ and add Xfce to the gdm session list.

---

