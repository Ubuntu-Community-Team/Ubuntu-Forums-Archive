---
title: "Window issues for one user"
date: 2011-09-16
forum: General Help
---

### Post by Ekeout on 2011-09-16
Running xubuntu 11.04 on an older HP laptop. Has worked fairly well for some time, but suddenly (I don't know what changed to cause it) the graphics for one user account messed up.

Alt-tab does nothing visible, windows do not have the top bar that you can drag around them with. Opening a terminal window is pointless because the window never gets focus so you can't enter anything into it.

It's the same whether I choose Xfce or Xubuntu session when I log in with this account.
Another user account does not have this issue.

Starting recovery mode - low graphics mode - everything works ok for this user.

What to do?

---

### Post by Toz on 2011-09-16
Sounds like the window manager has crashed. For that specific account, press Alt+F2 and run the following command:
```
xfwm4 --display=:0.0 --replace
```

---

### Post by Ekeout on 2011-09-17
That did it!

I'll learn more about the command later, and for now we can say I created a new instance of the xfwm4 window manager and made it actve, I think?

Thanks, anyway.

---

### Post by Toz on 2011-09-17
> **Ekeout said:**
> That did it!

I'll learn more about the command later, and for now we can say I created a new instance of the xfwm4 window manager and made it actve, I think?Yes. You restarted the window manager that manages the desktop windows.

> Thanks, anyway.
Can you please mark this thread as solved from the Thread Tools link above? Thanks.

---

