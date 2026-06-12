---
title: "Installing Ubuntu from Kubuntu? Please Help?"
date: 2010-01-26
forum: General Help
---

### Post by THE GMoD on 2010-01-26
I am having some trouble with Kubuntu (As some of you that seen my earlier thread from today... then again its been a few hours and that thread is now PAGES away?) 
I need some way of installing Ubuntu from Kubuntu without having to burn the .iso from a disk... I have no blank disks so I really need help here...
WHY do I have such bad luck with threads here? Someone created a thread literally seconds after this one and its got... 49 views or something, this one had NO views...

---

### Post by adam814 on 2010-01-26
```
sudo apt-get install ubuntu-desktop
```

That will install GNOME and all the other dependencies for a standard Ubuntu install.  You'll have an option to choose between gdm and kdm as a display manager.  You want gdm.

Then restart X (CTRL+ALT+Backspace does it for me, I think it's configurable in System > Preferences > Keyboard > Layouts > Options).

Once you're able to log in and use GNOME without problems you can remove the leftover Kubuntu packages.  Follow these instructions if you're using Karmic (if not there are links on the page): [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by adam814 on 2010-01-26
> **THE GMoD said:**
> WHY do I have such bad luck with threads here? Someone created a thread literally seconds after this one and its got... 49 views or something, this one had NO views...Haha, next time I'll type faster. :p

---

