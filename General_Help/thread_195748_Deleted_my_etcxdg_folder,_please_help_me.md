---
title: "Deleted my /etc/xdg folder, please help me"
date: 2006-06-13
forum: General Help
---

### Post by glotz on 2006-06-13
Hi there. I posted this thread originally in *absolute beginner questions* but it hasn't received any answers in 7 hours, so I guess I'll try here too...

I'd really appreciate you helping me!

Here's the thread [http://www.ubuntuforums.org/showthread.php?t=195560](http://www.ubuntuforums.org/showthread.php?t=195560)

---

### Post by glotz on 2006-06-13
Anybody??

---

### Post by mlind on 2006-06-13
Have you tried reinstalling package that provides /etc/xdg folder contents ?
You need to atleast reinstall gnome-menus, gnome-power-manager, gnome-volume-manager and update-notifier packages.

```

sudo aptitude reinstall gnome-menus gnome-power-manager gnome-volume-manager gnome-screensaver update-notifier

```

Here's how I checked that
```

dpkg -S /etc/xdg/*.*
gnome-menus: /etc/xdg/menus/applications.menu
gnome-menus: /etc/xdg/menus/settings.menu
update-notifier: /etc/xdg/autostart/update-notifier.desktop
gnome-volume-manager: /etc/xdg/autostart/gnome-volume-manager.desktop
gnome-screensaver: /etc/xdg/menus/gnome-screensavers.menu
gnome-power-manager: /etc/xdg/autostart/gnome-power-manager.desktop
gnome-menus: /etc/xdg/menus/preferences.menu

```

---

### Post by glotz on 2006-06-14
Thank you for your reply. Unfortunately, it didn't work. It did create the xdg folder and subfolders menus and autostart but autostart was empty and menus only contained a debian-menu.menu which was a broken link.

---

### Post by mlind on 2006-06-14
[QUOTE=glotz]Thank you for your reply. Unfortunately, it didn't work. It did create the xdg folder and subfolders menus and autostart but autostart was empty and menus only contained a debian-menu.menu which was a broken link.[/QUOTE]

You are right, those files didn't came back..

This works though
```

sudo aptitude purge gnome-menus gnome-power-manager gnome-volume-manager gnome-screensaver update-notifier

```

accept the relution aptitude prompts.

```

sudo aptitude install ubuntu-desktop

```

keep note on what dependencies purging removes, and make sure that after
installing ubuntu-desktop, these are back.

---

### Post by glotz on 2006-06-14
Thanks. I didn't get it working though. You're probably right about that it could be done that way. Just not by me. I guess I'll just be reinstalling.

This oughta teach me not to delete random folders...

---

### Post by josys36 on 2006-07-26
Having the same issue and the suggested suggestions did not work.

Jason

---

### Post by mlind on 2006-07-26
> **josys36 said:**
> Having the same issue and the suggested suggestions did not work.

Jason

Do you mean you also deleted /etc/xdg folder contents?

---

### Post by josys36 on 2006-07-27
Yep, and all the suggestions I have tried on the forum don't seem to be able to deal with the problem.

I was however able to get XFCE working completely, but KDE and Gnome have lost their menus. Good thing for me that I had shortcuts to all the normal apps I use up in the panels.

Jason

---

### Post by mlind on 2006-07-27
> **josys36 said:**
> Yep, and all the suggestions I have tried on the forum don't seem to be able to deal with the problem.

I was however able to get XFCE working completely, but KDE and Gnome have lost their menus. Good thing for me that I had shortcuts to all the normal apps I use up in the panels.

Jason

Did you try purging gnome-menus, gnome-power-manager, gnome-screensaver gnome-volume-manager and update-notifier ? And then reinstalling those back?

---

### Post by kevin2849 on 2006-11-19
I did this recently and did not want to re-install. My solution was to load up my live CD of Edgy and copy the XPG folder onto a flashdrive. I then rebooted into my regular system and transfered the folder into /etc/. You need to be root to do this. Hope this helps.

---

