---
title: "Gnome terminal wont start"
date: 2006-02-07
forum: General Help
---

### Post by darkfusion on 2006-02-07
I was messing around with getting my terminal to be borderless and in my profile I added a cmd to start with everytime the terminal starts  . But now I cant get my terminal to start it justs opens then closes . Any idea how I can fix this ? Thanks

---

### Post by z_diver on 2006-02-07
I think you can just delete/rename the profile can't you?  Look in ~/.gconf/apps/gnome-terminal/profiles.  If not maybe one of the files in /etc/gconf/gconf.xml.defaults/apps/gnome-terminal/ will do it.

slocate gnome-terminal|grep conf
will provide a list of possibilities.

---

### Post by darkfusion on 2006-02-07
Hey thanks that worked . I just edited the xml file in the profile .

---

