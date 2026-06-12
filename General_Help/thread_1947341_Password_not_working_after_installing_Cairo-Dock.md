---
title: "Password not working after installing Cairo-Dock"
date: 2012-03-26
forum: General Help
---

### Post by Asfakul on 2012-03-26
Hello,

My password is not being recognized after installing Cairo-Dock.
 I selected cairo dock in the login menu and my password is not working since then. It getting struck while loading desktop and reverting back to login screen.

I tried login using normal ubuntu but to no avail. 


Please help!

---

### Post by jerome1232 on 2012-03-26
The problem isn't your password, it sounds like cairo-dock is causing your session to crash. Did you install it with apt-get? 

Try dropping to a command line and removing cairo-dock (ctrl+alt+f1) (ctrl+alt+f7 to get back to your login screen)

```
sudo apt-get remove --purge cairo-dock
exit
```

That should at least get your interface working again.

---

### Post by Asfakul on 2012-03-27
Thanks Jerome .

How can i get to a terminal from Login screen?

---

### Post by tmx84 on 2012-03-27
Exactly as he explained above, ctrl-alt-f1 will take you to a terminal where you can login then remove cairo-dock, then once you are finished removing it, press ctrl-alt-f7 which will take you back to your login screen.

---

