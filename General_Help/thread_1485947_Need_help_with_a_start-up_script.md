---
title: "Need help with a start-up script"
date: 2010-05-17
forum: General Help
---

### Post by sleepitoff on 2010-05-17
I need the keys alt+shift+f12 pressed after I log in. What would this code be? 

In system preferences, there's an option to add custom scripts to start up, so I just need the code for it.

---

### Post by blazemore on 2010-05-18
lol, that isn't a solution to the problem, that's a solution to the symptom!

I'm going to make a massive assumption that your desktop effects are being suspended on login.
If you want to fix that, it's easy. There's a file which contains a line overriding your setting, and forcing KDE to suspend compositing.

You can delete the file by opening a terminal ("Konsole") and trying this:

```
mv ~/.dmrc ~/.dmrc.old
```

This should have no adverse effects

---

