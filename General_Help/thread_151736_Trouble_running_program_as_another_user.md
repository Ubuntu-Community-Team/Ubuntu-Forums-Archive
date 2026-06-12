---
title: "Trouble running program as another user"
date: 2006-03-28
forum: General Help
---

### Post by speedsix on 2006-03-28
MythTv sets up a separate user 'mythtv'. I want to run the program from my regular login. This works if I choose the System Tools->Run as a Different User and select the mythtv user from the list.

I want Mythtv to launch on boot, I've tried sudo -u mythtv mythfrontend but this comes up with some sort of xserver error. Obviously I need to be able to run it without putting the mythtv username in every time.


Many thanks

---

### Post by az_human on 2006-03-28
Do you have the option of NOT creating a separate user account when you install MythTV?

---

### Post by schilcha on 2006-03-28
try wrapping the "sudo ..."-line in a script:
```

#!/bin/sh
xhost +local:
sudo -u mythtv mythfrontend

```

The xhost-line will allow the user mythtv to display its window on your display. If you need to supply a pwd for the user mythtv, you can configure sudo to let you launch mythfrontend without supplying a pwd. 

Good Luck!

---

