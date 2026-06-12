---
title: "Where are Startup Applications stored?"
date: 2011-08-22
forum: General Help
---

### Post by Kissell on 2011-08-22
I need to be able to launch a GUI application for all users after they login.  I know I can go to Startup Applications and add a launcher, but I don't want to have to login as every user and do that.  Is there a file I can edit from the command line with elevated privledges?  Something I could script, like appending to an XML file or something?

---

### Post by dave01945 on 2011-08-22
you need to make desktop shortcuts in 

```
/etc/xdg/autostart/
```

or you can use

```
~/.config/autostart
```

but that is user specific

---

### Post by Kissell on 2011-08-22
Beautiful, I already have some .desktop files I copy to their Desktops, so I can just place them in /etc/xdg/autostart

That should work wonderfully!  Thank you so much!

---

