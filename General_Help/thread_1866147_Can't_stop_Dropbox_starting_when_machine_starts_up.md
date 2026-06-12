---
title: "Can't stop Dropbox starting when machine starts up"
date: 2011-10-21
forum: General Help
---

### Post by keevill on 2011-10-21
I can't seem to be able to stop Dropbox starting automatically when my machine starts up.
I've tried going into system/preferences/startup apps and unchecking and even deleting Dropbox but it comes back upon a restart.
Normally this wouldn't be a problem except that the Dropbox folder is located on a different partition and this partition needs to be mounted prior to opening Dropbox or we get the error message that the Dropbox folder is missing.
Ubuntu 10.04 32Bit.
-keevill-

---

### Post by crazy bird on 2011-10-21
Did you also checked under System > Administration > Startup Manager? It might be that it is still there. Just uncheck it will prevent Dropbox starting up automaticly the next time you boot your system.

---

### Post by keevill on 2011-10-21
> **crazy bird said:**
> Did you also checked under System > Administration > Startup Manager? It might be that it is still there. Just uncheck it will prevent Dropbox starting up automaticly the next time you boot your system.

Startup Manager ?? I Don't have that in the System > Adminstration
Doesn't that just control the order of the boots in a dual boot system ??
-keevill-

---

### Post by crazy bird on 2011-10-21
I am not quit sure how it is called in the English version of Ubuntu, but you have to look in System > Administration or System > Preferences. There's a button for startup manager or similiar to that. It will show you a list of program's which will be started up during booting Ubuntu. In that list there's also an entry for Dropbox.
 
 
> Startup Manager ?? I Don't have that in the System > Adminstration
Doesn't that just control the order of the boots in a dual boot system ??
-keevill-
That's called a boot manager.

---

### Post by keevill on 2011-10-21
> **crazy bird said:**
> I am not quit sure how it is called in the English version of Ubuntu, but you have to look in System > Administration or System > Preferences. There's a button for startup manager or similiar to that. It will show you a list of program's which will be started up during booting Ubuntu. In that list there's also an entry for Dropbox.


I believe that's where I have disabled Dropbox startup. In my version its in
System>Preferences>Startup Applications.

-keevill-

---

### Post by keevill on 2011-10-21
Now, it seems that by disabling this startup, Dropbox no longer start automatically. 
2 tests so far.
-keevill-

---

