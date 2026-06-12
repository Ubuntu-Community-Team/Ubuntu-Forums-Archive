---
title: "Verbose boot not working- 11.04, acer aspireone"
date: 2011-10-20
forum: General Help
---

### Post by somedaypilot on 2011-10-20
Hello,
I wanted to get more than a bunch of blinking dots on screen during boot as an attempt to figure out more of what actually goes on behind the scenes, so searching google for "ubuntu verbose boot" eventually led me to [https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29) and the GRUB_CMDLINE_LINUX_DEFAULT= option in /etc/default/grub. However, when I changed it from "quiet splash" to "splash" ran update-grub and restarted, it booted with a blank ubuntu-purple screen instead of any kind of output. No splash screen, no text output, nothing but dark purple until suddenly the login screen. It continues to do this after changing the option back to "quiet splash", to "", and to "splash" again. The only ohter thing I can think of that may be relevant is that I used gksu gedit to edit things at first and got the GTK-warn thing that's been happening in 11.04. I've since tried editing with sudo nano, and still get the same results. I am running Gnome 11.04 on an acer aspireone netbook/laptop/craptop.

---

### Post by oldos2er on 2011-10-20
Try changing that line GRUB_CMDLINE_LINUX_DEFAULT="splash" to GRUB_CMDLINE_LINUX_DEFAULT="text"

---

### Post by somedaypilot on 2011-10-23
It broke boot. I was able to get it back to the previous state by using tty1, but only after normal boot failed. The only thing that I could see failing was "disable auto-update" or something like that. It's still not doing what I want, but at least I have GNOME back.

---

