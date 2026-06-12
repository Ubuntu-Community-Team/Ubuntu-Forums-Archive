---
title: "problem logging on"
date: 2009-08-01
forum: General Help
---

### Post by windsorhelpdesk on 2009-08-01
Hello,

I am having problem logging on to ubuntu 9.04.  When I type my user name and hit enter the screen goes blank and acts like it is going to go to the password box, but then it reverts me back to entering my user name.  I have made a new user name in recovery mode and still it does not work.  I am running ubuntu 9.04 64 bit addition on a Toshiba laptop.  Any help would be appreciated.

Thanks,
windsorhelpdesk

---

### Post by SEMW on 2009-08-01
If you're absolutely sure that you're typing in your username correctly (in the correct case, it is case-sensitive), try logging in in text mode and see if that works.  Press ctrl+alt+F1, and you'll see a text prompt asking you to enter your username; try logging in with that.  If that works, then there's a problem with GDM (the graphical login screen).

---

### Post by windsorhelpdesk on 2009-08-01
The text prompt log in worked.  I successfully logged in as my user name any ideas on how to fix the log in screen?

Thanks,
windsorhelpdesk

---

### Post by SEMW on 2009-08-01
Try (whilst logged in at the text prompt): ```
sudo apt-get purge gdm && sudo apt-get install gdm ubuntu-desktop
```

This will reinstall the graphical login screen.  (ubuntu-desktop is a meta-package -- a package that has nothing but depends on other packages -- that is removed if you remove gdm, so needs to be readded)

---

