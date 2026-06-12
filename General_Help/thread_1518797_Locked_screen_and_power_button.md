---
title: "Locked screen and power button"
date: 2010-06-27
forum: General Help
---

### Post by jruhill on 2010-06-27
In Ubuntu 10.04: if the screen has been locked (automatically by the screensaver or user-activated using the top-right menu) pressing the power button doesn't initiate shutdown. Is this a bug or is it a configurable option?

I would expect to either get the usual 60 second shutdown delay or a graceful shutdown right away.

---

### Post by dino99 on 2010-06-27
set the screensaver prefs

---

### Post by tombert on 2010-10-20
Hi there ... same problem ... the screensaver does not have any options about that ...
already edited the polkit ... but not with success.
Did you found any solution to that?

thx

---

### Post by tombert on 2010-10-20
ok - I did the hammer method:

/etc/acpi/powerbtn.sh
put shutdown in the top line.

thx

---

