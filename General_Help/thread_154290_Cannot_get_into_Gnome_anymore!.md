---
title: "Cannot get into Gnome anymore!"
date: 2006-04-02
forum: General Help
---

### Post by tico on 2006-04-02
Hi everybody,

Today I made some upgrades in Ubuntu using Automatix. After having installed Firefox 1.5, Thunderbird 1.5 and the plugins for mp3 and DVD, I uninstalled Evolution Mail and OpenOffice (I would install version 2.0). After having rebooted, I cannot get into Gnome anymore.
After the login screen, the gnome desktop stops loading and it hangs on the brown background. I can move my mouse pointer but there's no way to use Gnome. Could you please help me to repair this whitout formatting and reinstalling?

TIA

---

### Post by aysiu on 2006-04-02
I'm not 100% sure, but I believe removing Evolution could have been bad. Try this:

1. Press Control-Alt-F1
2. Log in
3. Type ```
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
exit
```
4. Press Control-Alt-F7
5. Press Control-Alt-Backspace

---

### Post by tico on 2006-04-02
It worked! Thanks a lot for your help.

---

### Post by x5452 on 2006-04-09
i just found this post while searching for a way to fix my problem.  I uninstalled Evolution because it was taking up a lot of memory. Then after reboot i got the brown screen, so I followed advice in this post, sudo apt-get install --reinstall ubuntu-desktop   it seams to be working and reinstalling now.  My question is, what the hell is evolution??? I thought it was just a mail client, why does uninstalling it take everything with it?  and why does it take up so much memory?

---

