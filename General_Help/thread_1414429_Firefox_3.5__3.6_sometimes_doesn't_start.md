---
title: "Firefox 3.5 / 3.6 sometimes doesn't start"
date: 2010-02-23
forum: General Help
---

### Post by yavoh on 2010-02-23
Running 9.10/Karmic.  This is reproducible with both FF3.5 from the repositories and FF3.6 from the mozilla-stable ppa.

(1) Firefox starts successfully.
(2) Close Firefox.
(3) Attempt to open firefox again.  Nothing happens, no command-line errors (except Glib warnings that don't affect operation)
(4) Start firefox in safe mode
(5) Exit Firefox.
(6) Go back to step (1).

I've tried reinstalling xulrunner and firefox, including doing a complete removal first.  I've tried clearing out my profile and that will work for a little while, and then it will stop again.  Any ideas?

---

### Post by lovinglinux on 2010-02-23
I have seen the same problem with another user, but I can't find the thread right now. 

Reinstalling xulrunner won't help, since Firefox 3.6 does not use the system xulrunner package. So I guess is not a xulrunner problem.

Have you tried to kill *firefox-bin* process after closing it?

What happens if you start firefox with this command:

```
firefox -P
```

Anyway, since cleaning your profile helps for a while, it might be something related to the profile lock file. Delete it after closing Firefox and making sure the *firefox-bin* process is not running in the background.

---

### Post by lovinglinux on 2010-03-02
If you have Prism installed, remove it. It is causing exactly that problem.

---

### Post by Leonivek on 2010-03-06
> **lovinglinux said:**
> If you have Prism installed, remove it. It is causing exactly that problem.

Thank you! :eek: This was bugging me for 2 weeks!  My main browser is Chromium, but sometimes Firefox is needed.  Removing Prism fixed the problem.

---

### Post by linooso on 2010-05-08
I have the same problem on Ubuntu 10.04, 32-bit, Firefox 3.6.3. The "firefox-bin" process is not terminated when I close the Firefox windows. Prism is NOT installed. I have to manually kill the "firefox-bin" process to start Firefox again.

Any solution for those not using Prism?

/ Frans Lundberg, Stockholm

---

