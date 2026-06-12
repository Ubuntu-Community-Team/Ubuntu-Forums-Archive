---
title: "Problems with gdm session manager"
date: 2010-05-27
forum: General Help
---

### Post by sinosoidal on 2010-05-27
Hi,

Yesterday I have made updates to Lucid. 

Today when I turned on computer I couldnt have the login box.

I had to manually specify a login user to gdm conf.

It logs in but cant add panels to the taskbar.

No notifications panels, no clock, etc. Cant even add this panels by myself!

Is this a known bug? How can I resolve this?

Thx,

Nuno

---

### Post by sinosoidal on 2010-05-31
Hi,

A couple of days have passed and no answers to this thread... 

I'm really getting out of my mind with this. I can't do half of the things because of this problem.

I can't start thunderbird, i cant start synaptic. This is becoming very annoying. 

I have been googling around but can't find a solution to this.

This is obviously a bug in lucid and its update packages. This is working fine before the last update.

This is what I cant see in syslog:

May 31 10:23:32 EDG-BRG-PC24 kernel: [  122.672678] bonobo-activati[1622]: segfault at 1c4f ip 00d56fc4 sp bfad5658 error 4 in libc-2.11.1.so[c3c000+153000]
May 31 10:23:32 EDG-BRG-PC24 kernel: [  122.673001] gnome-panel[1620]: segfault at 4 ip 080ad2f9 sp bfbec7d0 error 4 in gnome-panel[8048000+83000]
May 31 10:24:58 EDG-BRG-PC24 kernel: [  208.992706] bonobo-activati[1784]: segfault at 1c4f ip 00350fc4 sp bfdeb0f8 error 4 in libc-2.11.1.so[236000+153000]
May 31 10:24:58 EDG-BRG-PC24 kernel: [  208.992933] gnome-panel[1624]: segfault at 4 ip 080ad2f9 sp bfd47630 error 4 in gnome-panel[8048000+83000]
May 31 10:25:20 EDG-BRG-PC24 kernel: [  230.571186] bonobo-activati[1798]: segfault at 1c4f ip 00b09fc4 sp bfe5b1e8 error 4 in libc-2.11.1.so[9ef000+153000]
May 31 10:25:20 EDG-BRG-PC24 kernel: [  230.571515] gnome-panel[1796]: segfault at 4 ip 080ad2f9 sp bf958e90 error 4 in gnome-panel[8048000+83000]
May 31 10:25:42 EDG-BRG-PC24 kernel: [  253.127153] synaptic[1804]: segfault at 1c4f ip 013c6fc4 sp bfdb22d8 error 4 in libc-2.11.1.so[12ac000+153000]
May 31 10:25:48 EDG-BRG-PC24 kernel: [  259.433196] synaptic[1814]: segfault at 1c4f ip 0468cfc4 sp bfb80198 error 4 in libc-2.11.1.so[4572000+153000]

Is anybody with the same problem? 

I have found other people with the same kind of problems with google, but no answers... 

Help....

Best regards,

Nuno

---

### Post by castawaybcn on 2011-09-18
edit:
deleted since the problem was not quite the same

---

