---
title: "Unable to change my keyboard layout"
date: 2012-04-24
forum: General Help
---

### Post by doesntcount on 2012-04-24
I've just upgraded to 11.10 but I made the huge mistake of choosing an English (UK) keyboard layout (I thought I was choosing language, not keyboard layout) during the installation.

This keyboard is not what I want. So I changed it in Gnome to English (US) which worked fine, but when I login to my xmonad window manager, it's still using the UK keyboard and I can't seem to figure out how to change it globally.

This thread seemed to have the same issue:

[http://ubuntuforums.org/showthread.php?t=951881](http://ubuntuforums.org/showthread.php?t=951881)

and solved it by "changing the keyboard at the login screen", however, I don't seem to be able to do this.

Anybody have any ideas on how to solve this?

Thanks.

---

### Post by doesntcount on 2012-04-25
Figured out the solution was to edit this:

/etc/default/keyboard

and change gb to us, then reboot.

---

