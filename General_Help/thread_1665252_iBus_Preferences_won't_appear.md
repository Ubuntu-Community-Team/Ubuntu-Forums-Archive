---
title: "iBus Preferences won't appear"
date: 2011-01-12
forum: General Help
---

### Post by danthemango on 2011-01-12
I'm learning Japanese, and I'm trying to configure iBus for that. Yet when I press on iBus Preferences, it shows in the window list as "Starting IBus Preferences", which then disappears revealing nothing. 
I've tried; 
```
ibus-setup
```
which yields 
```
Traceback (most recent call last):
  File "/usr/share/ibus/setup/main.py", line 28, in <module>
    import gtk
ImportError: No module named gtk
```

I installed python-gtk2, yet the problem persists. 
```
ibus-daemon
```
says it's already running, but no icon is showing.

I don't know if it's relevant, but I installed scim not knowing ibus does the same thing. 
I tried;
```
sudo apt-get install ibus -f
```

I have no idea what to do, or what's wrong, hope any of you know.

---

### Post by danthemango on 2011-01-12
ok, ignore the first problem, how do I get gtk to import into python? Google isn't being my friend right now.

---

### Post by karthick87 on 2011-01-12
What version of ubuntu you are using?

---

### Post by danthemango on 2011-01-12
> **karthick87 said:**
> What version of ubuntu you are using?

10.04 Lucid Lynx.

---

### Post by CanolaOil on 2011-01-14
FWIW, I'm having the same issue.

---

