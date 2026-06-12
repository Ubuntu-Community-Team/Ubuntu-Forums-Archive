---
title: "How do I remove KDE"
date: 2009-11-30
forum: General Help
---

### Post by kevinwmiller on 2009-11-30
Oh, it's so terrible.  I wish I would've never installed the thing!  It's hideous in looks too, these bubbles things.

Anyways, I installed with synaptic.

Any ideas?

---

### Post by Cheesemill on 2009-11-30
If you installed the kubuntu-desktop package you can get back to just gnome by following the instructions here:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by kevinwmiller on 2009-11-30
Ok, there is still a "Kubuntu" boot-up load screen, and now there isnt a log-in screen.

Wha happened?

---

### Post by kevinwmiller on 2009-11-30
Ok, I was wrong.  If I log out, there is a Login screen, and it no longer has KDE as an option.

There is still the extra "kubuntu" boot load screen that takes up time that I'd like gone, what do you think?

Can't wait to get back to sweet, glorious GNOME.

---

### Post by LordIshamael on 2009-11-30
If you mean the original loading screen before the login screen, then try installing startupmanager.

[http://ubuntuforums.org/showthread.php?t=1275939](http://ubuntuforums.org/showthread.php?t=1275939)

I think this guy wanted the same thing...

Edit: Sorry, startup-manager is the package name.

---

### Post by kevinwmiller on 2009-11-30
How do I install startup-manager, its not in the software center.

---

### Post by LordIshamael on 2009-11-30
In a terminal, put ```
sudo apt-get install startupmanager
```

Some packages are not listed as applications in the software centre, but rather as individual packages.

Hmmm... apparently the package name is startupmanager after all...

Sorry, it was mentioned as otherwise elsewhere.

Edit: You might find this helpful...

[http://www.addictivetips.com/ubuntu-linux-tips/how-to-install-and-use-ubuntu-startup-manager/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-install-and-use-ubuntu-startup-manager/)

---

### Post by kevinwmiller on 2009-11-30
It was in the software center, I must of overlooked it.  Thanks, it solved the problem.

---

### Post by mrebanza on 2010-09-19
```
sudo apt-get autoremove kde-window-manager

sudo apt-get autoremove kubuntu-desktop
```

does half the job but your still stuck with all the kde software like Konqueror . . . I am on 10.10 beta . . . I can't seem to get rid of KDE :confused:

---

### Post by wilee-nilee on 2010-09-19
Actually you can install multiple desktops and choose which one you want at the login screen. But programs that work in kde that would work in another desktop will be there.

---

### Post by gandaran on 2010-09-19
> **mrebanza said:**
> ```
sudo apt-get autoremove kde-window-manager

sudo apt-get autoremove kubuntu-desktop
```

does half the job but your still stuck with all the kde software like Konqueror . . . I am on 10.10 beta . . . I can't seem to get rid of KDE :confused:
open synaptic package manager and type "qt" in search box.
I run a pure gnome environment, I dont have a single qt lib installed and never will.
if you dont need to run any KDE application just remove all the qt libs installed, mark them for complete removal and click the apply button, that should remove everything related to KDE.

---

### Post by wilee-nilee on 2010-09-19
libqt4 supports these, just in case you have them but you will see whats up when you try to remove anything.
[ATTACH]169928[/ATTACH]

---

