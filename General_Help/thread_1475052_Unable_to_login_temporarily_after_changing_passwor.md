---
title: "Unable to login temporarily after changing password in GUI in 9.10"
date: 2010-05-06
forum: General Help
---

### Post by Nakor BlueRider on 2010-05-06
Just wanted to know if anyone experienced this before, or how to avoid it in the future.  I changed my password from the:

System > Administration > Users and Groups > My Account > Properties... > Change Password

...option, but other than the Users and Groups dialogue itself, all other things (like the package manager) required my old password.  I rebooted, and when I tried to log in, the new one came up wrong and the old one resulted in a string of errors starting with "Could not update ICEauthority file /home/myaccount/.ICEauthority" followed by errors loading directories like ~/Desktop and Gnome Desktop failing to start.

I was able to fix it by using the Ctrl-Alt-F1 terminal, logging in with the old pass and changing it to the new one using the chpasswd command; that, followed by a reboot, fixed the problem.

I wasn't sure if this was a bug or if the Users GUI wasn't meant for changing the current user's password, so I thought I'd ask here.  TIA.

---

