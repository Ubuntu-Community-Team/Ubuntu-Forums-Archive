---
title: "Caffeine on Kubuntu 12.04 (64-bit) not working"
date: 2012-04-29
forum: General Help
---

### Post by MrsUser on 2012-04-29
Hello, I'm a new user to the Linux world. I installed Kubuntu. So far I love it. But I got annoyed by the screensaver kicking in while watching flash videos on Youtube. So I googled, found Caffeine and installed it. However, Caffeine crashes when trying to start it. Anyone got the same problem or a solution to this?

I got the Caffeine deb from here:
[https://launchpad.net/~caffeine-developers/+archive/ppa]("https://launchpad.net/%7Ecaffeine-developers/+archive/ppa")

---

### Post by Humanity for Others on 2012-04-29
You can change the screensaver timing by going to System Settings, Display Monitor (in the hardware section).

---

### Post by oldos2er on 2012-04-29
MrsUser, the same thing occurs on my system, this is the error: ```
ERROR:root:Could not find any typelib for AppIndicator3
ERROR:root:Could not find any typelib for Notify
Please install pynotify
ERROR:root:Could not find any typelib for Notify
Traceback (most recent call last):
  File "/usr/bin/caffeine", line 40, in <module>
    import caffeine
  File "/usr/bin/../share/pyshared/caffeine/__init__.py", line 154, in <module>
    from caffeine.main import main
  File "/usr/bin/../share/pyshared/caffeine/main.py", line 47, in <module>
    import core
  File "/usr/bin/../share/pyshared/caffeine/core.py", line 21, in <module>
    from gi.repository import Gtk, GObject, Gio, Notify
ImportError: cannot import name Notify
```

There's an email address at the top of the page [https://launchpad.net/~caffeine-developers](https://launchpad.net/~caffeine-developers) where you can inquire about the bug.

---

### Post by MrsUser on 2012-04-29
> **Humanity for Others said:**
> You can change the screensaver timing by going to System Settings, Display Monitor (in the hardware section).

I did that. Switched off screensaver completely. Also went to power settings and disabled switching off monitor. But the screen still goes black after 10 minutes. The settings in KDE do not have any effect. I assume it's a bug. Therefore, I wanted to install Caffeine.

---

### Post by MrsUser on 2012-05-02
Nevermind. I re-installed my OS. Wiped Kubuntu and replaced it with Ubuntu 12.04. Unity gets another chance. I'll see if I need Caffeine and if it works.

---

