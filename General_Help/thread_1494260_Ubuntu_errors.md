---
title: "Ubuntu errors"
date: 2010-05-26
forum: General Help
---

### Post by DJH91 on 2010-05-26
When i turn on my computer i get 2 or 3 errors while ubuntu is loading up and i have to press ok. When it finnaly gets to the desktop it stops with no panels or nothing and has the purple background picture (which isn't even my desktop background:confused:) I can't even right click but the mouse cursor is there. Is there anyway i can run a command or something to re-install or something? Basically put it back to how it was when i first installed it.

---

### Post by jerenept on 2010-05-26
Is any of these errors 'Could not update ICEAuthority file /home/youruser/.ICEAuthority'
Then you are, in my experience, better off making a new user account.

---

### Post by DJH91 on 2010-05-26
> **jerenept said:**
> Is any of these errors 'Could not update ICEAuthority file /home/youruser/.ICEAuthority'
Then you are, in my experience, better off making a new user account.

Yep -- but how? I can't do anything. :( Is there a command?

---

### Post by marshmallow1304 on 2010-05-26
Boot into recovery mode (hold Shift during startup then select the first recovery mode option) and run
```
chown -R <username>:<username> /home/<username>/.*
```
Where <username> is your username.

---

