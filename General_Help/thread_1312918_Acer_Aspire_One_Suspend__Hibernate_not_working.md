---
title: "Acer Aspire One Suspend / Hibernate not working"
date: 2009-11-03
forum: General Help
---

### Post by Dom3 on 2009-11-03
I have an Acer Aspire One ZG8 netbook and recently upgraded from Jaunty to the full version of Karmic (not UNR). Since the upgrade, suspend and hibernate have stopped working.

Both "appear" to work, but the computer never actually suspends/freezes, it just locks up - requiring a hard reset to restart. I can't see anything obvious in the log files, and the same computer worked fine under Jaunty.

Any ideas?

---

### Post by canoo on 2009-11-03
I have a similar problem. Just wiped 9.04 minimal for 9.10 minimal (both using xfce4 with the gnome-power-manager). 

I could use the command
```
sudo pm-suspend
```
in 9.04 to suspend. In 9.10 if i execute that command the computer thinks for a second then locks up and i have to do a hard reboot.

---

### Post by Dom3 on 2009-11-07
Anyone any idea at all?

---

### Post by Dom3 on 2009-12-05
Still not having any luck with this at all. I can't be the only one... anyone?

---

### Post by imota on 2010-09-13
I am having similar problems on my Acer Aspire 5553G. You can see another lengthy thread that might have some suggestions... I haven't had any luck with them yet, still looking for a solution!

[http://ubuntuforums.org/showthread.php?t=1469340](http://ubuntuforums.org/showthread.php?t=1469340)

---

### Post by karlwilbur on 2010-12-25
Found this:
[http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/](http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/)

It might help.

---

