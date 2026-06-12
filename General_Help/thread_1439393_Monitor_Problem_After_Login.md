---
title: "Monitor Problem After Login"
date: 2010-03-26
forum: General Help
---

### Post by beamendslrs on 2010-03-26
Hi All,
I have a rather odd problem with a machine. Up until the user logs in everything is fine, but as soon as they log in the display breaks up rendering the computer unusable. Booting from CD is ok, but the monitor is not detected. Any ideas?

---

### Post by 666f6f on 2010-03-26
Propably X is misconfigured. Can you try the following command and see if it helps?

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

P.S. If you can not take any further action because the screen is all messed up, you can either boot in failsafe mode, or press Ctrl+Alt+F1 while being on (the messed up) login screen.

---

### Post by beamendslrs on 2010-03-26
> **666f6f said:**
> Propably X is misconfigured. Can you try the following command and see if it helps?

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Hi,
yes I've tried that, and running  dpkg-reconfigure. It seems to be connected to the actual user, everything is fine until they log in. 

Is there some user preference that "overrides" xorg.conf ?

---

### Post by realzippy on 2010-03-26
*Is there some user preference that "overrides" xorg.conf ?*

Maybe there is a file "monitors.xml" in /home/yourusername/.config/

which can be deleted/edited if exists...

---

### Post by beamendslrs on 2010-03-26
> **realzippy said:**
> *Is there some user preference that "overrides" xorg.conf ?*

Maybe there is a file "monitors.xml" in /home/yourusername/.config/

which can be deleted/edited if exists...

I cant find one - I've had a look for anything x11ish as well.

---

