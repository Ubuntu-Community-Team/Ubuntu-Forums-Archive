---
title: "How do I stop user timeout?"
date: 2010-12-12
forum: General Help
---

### Post by DemonRedWolf on 2010-12-12
Whenever my computer's idle for about 2 minutes, it automatically goes to the login screen. How do I prevent this from happening?

---

### Post by Quackers on 2010-12-12
I can't get to it at the moment to check but I'm sure it's in Power Management. Take a look there :-) Possibly screensaver settings too.

---

### Post by DemonRedWolf on 2010-12-12
Okay, I did that, and it still does it. Does anyone else know?

---

### Post by Quackers on 2010-12-12
You may also need to press Alt + F2 and type in gconf-editor and press enter.
Then navigate to Apps > Gnome power manager > Lock and then in the right pane make sure "use_screensaver_settings" is ticked. I had to untick it then tick it again.
Then either reboot or log out and log in again.

---

### Post by DemonRedWolf on 2010-12-12
Did that, still keeps locking out.

---

