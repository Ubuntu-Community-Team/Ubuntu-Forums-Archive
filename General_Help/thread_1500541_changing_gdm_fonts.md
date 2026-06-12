---
title: "changing gdm fonts"
date: 2010-06-03
forum: General Help
---

### Post by mozi on 2010-06-03
Hi,

I would like to change gdm fonts in lucid to droid, how can I do it?

thanks

---

### Post by wojox on 2010-06-03
Log out

Ctrl+Alt+F1

Login and run these two commands

```

export DISPLAY=:0.0
sudo -u gdm gnome-control-center


```

Then Ctrl+Alt+F7 or F8

---

### Post by the8thstar on 2010-06-03
You don't need to log out. That command alone will do the trick:

> sudo -u gdm gnome-control-center

---

### Post by mozi on 2010-06-03
but in gnome-control-center, in the gdm options there is no option to change font

---

### Post by towheedm on 2010-06-03
> **mozi said:**
> Hi,

I would like to change gdm fonts in lucid to droid, how can I do it?

thanks

To change the fonts, use the following command:
```
sudo -u gdm dbus-launch gnome-appearance-properties
```

Click on the FONTS tab and select the fonts of your choice.

For a more comprehensive customization of GDM, check out the link at the beginning of this thread:
[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

Hope it works for you.

---

### Post by mozi on 2010-06-03
ok but this changes ubuntu desktop fonts, I have changed them but cannot change the fonts on the login screen

---

### Post by towheedm on 2010-06-03
> **mozi said:**
> ok but this changes ubuntu desktop fonts, I have changed them but cannot change the fonts on the login screen

Well this is strange, because the above command changes the fonts in the login screen (GDM).  I just double checked it in 10.04 and my fonts were changed.

Are you entering the entire command:
```
sudo -u gdm dbus-launch gnome-appearance-properties
```If you only enter:
```
gnome-appearance-properties
```only your desktop fonts will be changed.

---

### Post by mozi on 2010-06-06
thanks, it works :)

---

### Post by towheedm on 2010-06-08
> **mozi said:**
> thanks, it works :)

Glad it works.

---

