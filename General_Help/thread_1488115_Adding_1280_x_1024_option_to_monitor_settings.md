---
title: "Adding 1280 x 1024 option to monitor settings"
date: 2010-05-19
forum: General Help
---

### Post by ronjr49423 on 2010-05-19
Hi all, I am rather new to Linux and am running the new Ubuntu 10.04. Things are going fairly smooth but I would love to get back to the 1280 x 1024 screen resolution I had with XP. Can anyone tell me the simplest way to make that happen?

Thanks, Ron

---

### Post by SlidingHorn on 2010-05-19
Here's a pretty good tutorial on how to edit your xorg.conf file to allow larger resolutions: [http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")

---

### Post by cuberts on 2010-05-19
> **ronjr49423 said:**
> Hi all, I am rather new to Linux and am running the new Ubuntu 10.04. Things are going fairly smooth but I would love to get back to the 1280 x 1024 screen resolution I had with XP. Can anyone tell me the simplest way to make that happen?

Thanks, RonI really do not know how to make this happen, but I think that maybe this link will help:
[https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)

---

### Post by ronjr49423 on 2010-05-20
Well I tried the first thing listed by backing up config and this is the  message I get:"cp: cannot stat `/etc/X11/xorg.conf': No such file or directory"
Should I or can I proceed?

---

### Post by SlidingHorn on 2010-05-20
> **ronjr49423 said:**
> Well I tried the first thing listed by backing up config and this is the  message I get:"cp: cannot stat `/etc/X11/xorg.conf': No such file or directory"
Should I or can I proceed?

In my infinite wisdom, I had forgotten that newer versions of ubuntu don't use xorg.conf by default.  You can, however, create your own for customization.  Just run:

```
gedit /etc/X11/xorg.conf
```

It should open a blank page, and you can work from there.

---

### Post by jlaki on 2010-05-20
The simplest way is the "System -> Preferences -> Monitors" way.

Also, if you enabled any of the proprietary drivers, you might use their utilities. I'm sure that nVidia appears in the "System -> Administration" menu after installing it and I also think ATi has it's utility, but I'm not sure, as for the other manufacturers.

You maybe already tried these, but I had to mention it.

---

