---
title: "randomly logged in as restricted user"
date: 2010-07-19
forum: General Help
---

### Post by jorgose on 2010-07-19
Hi,
I have a very annoying problem with my Lucid (installed with ubuntustudio's alternate dvd). Two out of four times when I log in my account has some restrictions. I can't mount devices on nautilus and the shutdown button won't be displayed. If I log out and log in I see the restrictions again. Only restarting (with "sudo shutdown -r now" or so) may give me a normal session.
On the console works everything normal. I mean i can sudo with my password.

Has anybody a hint for me? Is this an issue of the ubuntustudio desktop? I use the generic kernel anyway...

---

### Post by cariboo on 2010-07-19
Make sure your user is in the following groups:

> adm dialout cdrom plugdev lpadmin admin sambashare

---

### Post by jorgose on 2010-07-20
Hi, I've checked that. The user is member of all those groups (when the session is normal). But i guess the problem goes on that direction. I have also noticed that if the WLAN LED already lights or blinks at the login window I will log into a normal session. Otherwise i'll login as a restricted user and after entering my password i'll be asked to enter it again to give wicd access to the network resources.

---

