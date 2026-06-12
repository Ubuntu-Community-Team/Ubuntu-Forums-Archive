---
title: "Unwanted Firefox startup"
date: 2009-12-20
forum: General Help
---

### Post by jimbob on 2009-12-20
Every time I start my system Firefox always starts too.   I do not have it in the startup preferences so I can't figure out what is starting it.
Thanks.

---

### Post by s.fox on 2009-12-20
Hello,

Only thing I can think  of that it might be is a script which is on autostart that launches Firefox.  

Can you give a list of programs in your autostart?

-Silver Fox

---

### Post by dcstar on 2009-12-20
> **jimbob said:**
> Every time I start my system Firefox always starts too.   I do not have it in the startup preferences so I can't figure out what is starting it.
Thanks.

Look in ~.config/autostart and remove any firefox.desktop file.

---

### Post by howefield on 2009-12-20
If the above doesn't sort it, try..

Close all running applications then go to System > Preferences > Startup Applications, and click on the Options tab, check "Automatically remember running applications when logging out".

Close and reboot.

Do it again, only uncheck the box this time.

---

### Post by jimbob on 2009-12-21
Thanks everyone - those suggestions did the trick.

---

