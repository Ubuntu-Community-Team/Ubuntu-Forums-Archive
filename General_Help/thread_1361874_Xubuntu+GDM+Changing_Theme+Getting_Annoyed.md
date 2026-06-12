---
title: "Xubuntu+GDM+Changing Theme+Getting Annoyed"
date: 2009-12-22
forum: General Help
---

### Post by User3k on 2009-12-22
Am I missing something here? I am trying to change the theme for my login screen in Xubuntu (64bit) Since Xubuntu is using GDM I am trying to do this through gdmsetup. But all that is there is the option to show the screeen for who will login, auto login and the seconds to autologin. Nothing else.

How do I either change the GDM theme or at least change the login image?

---

### Post by Brandon Williams on 2009-12-22
There have been plenty of threads about this. Searching the forum for 'karmic gdm config' uncovered, among other things, this [howto thread](http://ubuntuforums.org/showthread.php?t=1333683&highlight=karmic+gdm+config) about customizing the new gdm.

---

### Post by User3k on 2009-12-22
> **Brandon Williams said:**
> There have been plenty of threads about this. Searching the forum for 'karmic gdm config' uncovered, among other things, this [howto thread](http://ubuntuforums.org/showthread.php?t=1333683&highlight=karmic+gdm+config) about customizing the new gdm.


Searching this forum is a pain. I didn't try that combination, "karmic gdm config" but I did try many other combinations and I also searched Google. I have been using Linux long enough to know how to do this. Be nice if I searched for Xubuntu GDM login theme or screen and came up with something. 

Thanks for the how to link.

---

### Post by eval- on 2010-01-21
Searching might not have saved you anyway, since not only is the new gdm basically unconfigurable (on my Xubuntu), but the only gdm-2.20 breaks **** and left me with blank consoles for most the day.

That HOWTO link MIGHT work if I'd installed 120m of gnome-control-center for gnome-appearance-properties on my SSD (I run xfce).  Also, the handy: [https://launchpad.net/gdm2setup](https://launchpad.net/gdm2setup) did not change my gdm background.

Downgrading to 2.20 was a disaster, but finally works.  Everyone should know that /etc/init/gdm.conf needs to be changed so that 'gdm-binary' is /usr/sbin/gdm and that /etc/X11/default-display-manager must exist ("/usr/sbin/gdm").  Gosh I hope they fix these packages soon.

---

