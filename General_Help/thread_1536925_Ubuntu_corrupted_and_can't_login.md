---
title: "Ubuntu corrupted and can't login"
date: 2010-07-22
forum: General Help
---

### Post by aym00n on 2010-07-22
Hi all, 

I had a problem in installing python on my Ubuntu 10.04 and I tried to remove the old one using synaptic manager, but I found it removing more than 300 packages, not related to python, I couldn't cancel it, so I did something stupid, I restarted the machine, when it was restarting I heared a loud sound from the machine, and when it comes back again, the login screen was different and I couldn't login with any username, always require the password again, I will really appreciate if anyone can help me and suggest something to do, or tell me how to restore the system to earlier status?

Thanks in advance

---

### Post by sidzen on 2010-07-22
Count it a learning experience and reinstall.

Next time, before making changes, these may be helpful:
[http://stackoverflow.com/questions/142764/how-do-i-upgrade-python-2-5-2-to-python-2-6rc2-on-ubuntu-linux-8-0](http://stackoverflow.com/questions/142764/how-do-i-upgrade-python-2-5-2-to-python-2-6rc2-on-ubuntu-linux-8-0)

[http://www.onecore.net/how-topython-programming-under-ubuntu.htm](http://www.onecore.net/how-topython-programming-under-ubuntu.htm)

[http://ubuntuforums.org/showthread.php?t=413682](http://ubuntuforums.org/showthread.php?t=413682)

BTW, I never had a problem upgrading PERL.

---

### Post by aym00n on 2010-07-22
> **sidzen said:**
> Count it a learning experience and reinstall.

Next time, before making changes, these may be helpful:
[http://stackoverflow.com/questions/142764/how-do-i-upgrade-python-2-5-2-to-python-2-6rc2-on-ubuntu-linux-8-0](http://stackoverflow.com/questions/142764/how-do-i-upgrade-python-2-5-2-to-python-2-6rc2-on-ubuntu-linux-8-0)

[http://www.onecore.net/how-topython-programming-under-ubuntu.htm](http://www.onecore.net/how-topython-programming-under-ubuntu.htm)

[http://ubuntuforums.org/showthread.php?t=413682](http://ubuntuforums.org/showthread.php?t=413682)

BTW, I never had a problem upgrading PERL.

Thanks for your reply, but does anyone know a way to replace files or packages from live cd or something..

---

### Post by Theft42 on 2010-07-22
I say the easiest thing you can do is just a reinstall.. as it sounds like alot of stuff was removed.

---

### Post by petrus250 on 2010-07-24
If it says something about gnome-power-manager you have to reinstall if not then look around a bit more.

---

### Post by varunendra on 2010-07-24
As others have already said, making a clean (re)install would be the easiest & quickest (and perhaps the only guaranteed) solution for you.

Is there something you want to save from this current installation?

---

### Post by WorMzy on 2010-07-24
When presented with the login window, press Ctrl+Alt+F1 to switch to a tty, and see if you can log in there. If you can, run
```
sudo apt-get install ubuntu-desktop
```

Then restart.

Next time, take care over what you uninstall. Both Synaptic and apt-get should tell you what else will be removed along with the program you're trying to uninstall before you confim the uninstall, so pay attention to what it tells you. If it looks like it's going to uninstall a lot of other un-related packages, then the package you're trying to remove is a core package, and the rest of the system won't work without it.

---

