---
title: "My Computer won't login"
date: 2009-07-28
forum: General Help
---

### Post by ejh2163 on 2009-07-28
I turn my computer on, wait for the dell logo to pass by
and arrive at the ubuntu 8.04 LTS login screen.
I input my username and password and press enter.
I wait, the screen comes out cracked and brings me back to the login screen.

What is wrong with my system?
It won't log me on.

This happened right after i went to compiz to check the magnification application box. The screen cracked and rebooted.

---

### Post by munky99999 on 2009-07-28
IF you hold

CTRL-ALT-F1

It should give you a commandline login. Try to login thru that.

If you forgot the password or something you will see it then.

You might have display driver issues or something with the login screen. Where it's trying to tell you the password is wrong but it's buggy.

If you get past the commandline login. You should try a
```
dmesg
```

Then see if there are any errors.

You can also try debugging the display problems thru the commandline.


Sorry I cant help much more beyond that.

---

### Post by s3a on 2009-07-28
If you can login with the terminal then try doing:

sudo apt-get update && sudo apt-get dist-upgrade

that will download the updates and hopefully fix the bug if that's what it is. You should also consider filing a bug report.

---

