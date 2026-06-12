---
title: "login problem - can't write in english"
date: 2009-07-15
forum: General Help
---

### Post by multiman on 2009-07-15
hi

I installed ubuntu on the other PC in home before five months, no real problems occured until yesterday.

When we turned the computer on, and reached the login screen, we found that we can only write in arabic, while the username and the password are in english.

I tried to change the language by pressing Alt+Shift (as usual), and by chnging the language by choosing from the login screen options, and by restarting the PC again, shutting it off, ... etc. I simply tried everything I know to login, but I couldn't.

Is there any way to trick the login screen, so I don't have to face it?
Or is there any way to solve this problem so far?

---

### Post by geirha on 2009-07-15
Hit Ctrl+Alt+F1 to get to a console, and log in there.

Run:
```
sudo update-locale LANG=en_US.UTF-8 LANGUAGE=en_US:en
```

That should set the default language to US english. If you want a different variant, run "locale -a" to see all languages available (i.e. the ones currently installed)

Restart the login-screen
```
sudo /etc/init.d/gdm restart
```

---

### Post by multiman on 2009-07-15
OK, I pressed the combination as you said, but even in console the english letters are not shown. All I see are dots, it seems not to work

---

### Post by PGScooter on 2009-07-15
try typing "reset" , even if you think it shows up as dots, and press enter. Sometimes when my console is acting up that will set it right. I'm guessing it won't work, but it's worth a try.

---

### Post by multiman on 2009-07-15
Again, it did not work.

---

### Post by multiman on 2009-07-15
I desided to re-install ubuntu, and that will definitely solve my problem :D
Thanks for your help

---

### Post by PGScooter on 2009-07-16
Sorry to hear that there was no easy fix. But that's one thing that I love about linux. If you keep track of the packages you install (I like that better than just exporting the list of all installed packages), then it's super easy to get back up and running. Heck I'll re-install ubuntu every now and then just for kicks haha.

---

