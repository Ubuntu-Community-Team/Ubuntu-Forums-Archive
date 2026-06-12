---
title: "Screen does not lock anymore"
date: 2010-08-10
forum: General Help
---

### Post by tbraun on 2010-08-10
Hello!

Recently, my desktop cannot be locked anymore. Furthermore, after waking up from suspend, I am straight in the desktop, it does not ask me for my password anymore. The screensaver also does not activate anymore either.

Any idea what could be the problem?

I'm still using Ubuntu 9.10 on a Dell Latitude D820.

Thank you very much...

---

### Post by ubunterooster on 2010-08-10
the program ```
gnome-screensaver
``` is not running

---

### Post by kliljedahl on 2010-08-10
I have the opposite problem after upgrading to 10.04 from 9.10. I am now prompted to enter a password every time. If I leave for more than 5 minutes the screen is dark & I need to enter a password. I'd rather it not be locked & go straight to the desktop.

---

### Post by ubunterooster on 2010-08-10
For you, I would go to system>preferences>screensaver.

Uncheck the "lock screen" box

---

### Post by ubunterooster on 2010-08-10
> **tbraun said:**
> Hello!

Recently, my desktop cannot be locked anymore. Furthermore, after waking  up from suspend, I am straight in the desktop, it does not ask me for  my password anymore. The screensaver also does not activate anymore  either.

Any idea what could be the problem?

I'm still using Ubuntu 9.10 on a Dell Latitude D820.

Thank you very much...
See if gnome-screensaver is listed under system>preferences>startup applications.

---

