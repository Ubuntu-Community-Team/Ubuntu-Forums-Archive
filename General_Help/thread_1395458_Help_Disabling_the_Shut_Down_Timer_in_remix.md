---
title: "Help Disabling the Shut Down Timer in remix?"
date: 2010-01-31
forum: General Help
---

### Post by hankjr55 on 2010-01-31
There is no preferences option when I right click on my user name at the top right so I'm having trouble disabling the 60 sec timer that comes up when I shut my laptop down. Any ideas of how I can disable this timer another way?

---

### Post by quixote on 2010-02-02
If you're using karmic, start gconf-editor in terminal (Accessories > terminal, and "gconf-editor" is the command you run).  In gconf-editor, go to apps > indicator-session.  Tick suppress-logout-shutdown.

If you're in Jaunty, the right-click context menu is supposed to work. :(

---

### Post by hankjr55 on 2010-02-02
ok thanks alot i guess im in karmic but it worked

---

