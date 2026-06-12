---
title: "Auto-Login to Xubuntu 10,04"
date: 2010-10-04
forum: General Help
---

### Post by [Shawn] on 2010-10-04
Hey guys!
I press ALT+F2 and entered
```
gksudo gdmsetup
``` 
and got to the menu to edit the settings.
However when I get to the Login Settings, It won't let me do anything!
There's an Unlock button and a close button, I clicked the Unlock button and nothing
Happened! Please help!

---

### Post by smilodonis on 2010-10-04
Try this edit:

$ cat /etc/gdm/custom.conf 
[daemon] 
TimedLoginEnable=false 
AutomaticLoginEnable=true 
TimedLogin=user_You_want_to_login 
AutomaticLogin=user_You_want_to_login 
TimedLoginDelay=30

---

