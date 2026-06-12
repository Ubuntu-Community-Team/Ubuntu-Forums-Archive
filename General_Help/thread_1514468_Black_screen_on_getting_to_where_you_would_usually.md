---
title: "Black screen on getting to where you would usually login"
date: 2010-06-21
forum: General Help
---

### Post by Thorntoon on 2010-06-21
Heya people
So my problem is I recently upgraded my Graphics driver and shut down to log in to windows (yes i dual boot) About 10-15 min later i went to log ubuntu the splash/loading screen what ever you call it worked normally but on reaching the point where one would login I was presented with a Blank screen. Ctrl-alt-f1 also presents me with a blank screen.
I'm kinda a linux noob and any help will be greatly appreciated.

---

### Post by Lampi on 2010-06-21
I recommend you boot the rescue entry of your grub menu. This will bring you to a terminal prompt.

Now it's about reading the log files - /var/log/Xorg.0.log for one, please type:

```
grep "(EE)" /var/log/Xorg.0.log
```
this should give you some error output what went wrong with your graphic update, post them in here.

---

### Post by Thorntoon on 2010-06-22
Fixed :]

---

