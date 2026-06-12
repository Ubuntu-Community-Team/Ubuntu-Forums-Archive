---
title: "change context menu for nautilus in 11.10"
date: 2011-10-22
forum: General Help
---

### Post by newbiefly on 2011-10-22
i've recently upgraded to 11.10.

i just want to right click on a folder or group of folders and have "open with movie player" as an option. i achieved this years ago with nautilus actions.  but the option has disappeared with the upgrade to 11.10.  now nautilus actions configuration tool keeps crashing.

is there any other way?

thanks for your time reading this.

---

### Post by berstbest on 2011-10-24
Hey,

I had the same issue with nautilus actions after upgrading to 11.10. But there's another program which helped in my case. You can install 'nautilus scripts manager' in the software center. This program allows you to add scripts to the folder /usr/share/nautilus-scripts which can then be selected in your nautilus-context-menu.
Hope that helps.

---

### Post by Barbapa on 2011-11-26
Hi

I am the maintainer of Nautilus-Actions, and, first, I would want thank you a lot for supporting this application !!
Thanks, really.

I have worked on this bug, and the better explanantion I've found is a packaging issue (see [https://bugzilla.gnome.org/show_bug.cgi?id=664163](https://bugzilla.gnome.org/show_bug.cgi?id=664163)).

The compatibility issue that I mention is most probably also a bug somewhere, but I really cannot debug Gnome myself ;)

Regards
Pierre

---

### Post by jerrrys on 2011-11-26
@ Barbapa

You probably have more support than you know.  When something just works, no one talks about it :)

---

