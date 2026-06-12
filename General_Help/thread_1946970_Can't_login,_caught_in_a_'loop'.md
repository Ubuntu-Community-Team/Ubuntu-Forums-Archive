---
title: "Can't login, caught in a 'loop'"
date: 2012-03-25
forum: General Help
---

### Post by DougieFresh4U on 2012-03-25
When I enter my password  for Ubuntu and hit enter, it goes to a black screen and back to login screen. I can login via 'guest' session.
I have searched through forum and found similiar but not the same exact issue.
This is a triple boot machine.
I am sure it is something simple :p

Edit:logged in using 'guest' session of the problem install
**EDIT: solved by a fresh install**

---

### Post by Habitual on 2012-03-25
Without knowing what version of Ubuntu you are using...
In the past I'd Ctrl+Alt+F1 at the login screen and at a prompt login there as myself, then I'd
```
mv .gconf .gconf.org
mv .config .config.org
exit
```

then I'd Ctrl+Alt+F7? and login and the issue was gone.
NOTE: This resets your gnome environment (read Desktop Settings and preferences)  to 'default'.
I am NOT certain that these instructions are still valid on Ubuntu's newest releases, but someone will chime in here soon.

---

