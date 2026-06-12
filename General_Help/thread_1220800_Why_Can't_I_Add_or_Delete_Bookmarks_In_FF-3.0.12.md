---
title: "Why Can't I Add or Delete Bookmarks In FF-3.0.12?"
date: 2009-07-23
forum: General Help
---

### Post by Mark76 on 2009-07-23
It's driving me nuts :-x ](*,)

---

### Post by Johnny B on 2009-07-23
try FF-3.5.1

---

### Post by Mark76 on 2009-07-23
I did. That's screwed up in a different way (external links open in a new window, not a tab in the current window).

---

### Post by Johnny B on 2009-07-23
so what happens when you mess with the bookmarks?
are you using "organize bookmarks"?
any error messages?
if you run firefox from a terminal window then try moving bookmarks, it should print all errors

---

### Post by Mark76 on 2009-07-23
I tried running FF from a terminal window and got no error messages at all when I tried to delete all my bookmarks.

They were all back when I ran FF again. Of course.

---

### Post by lovinglinux on 2009-07-23
See **Solution** [*[COLOR="Red"]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003).

> **Mark76 said:**
> I tried running FF from a terminal window and got no error messages at all when I tried to delete all my bookmarks.

They were all back when I ran FF again. Of course.

Did you use the command "sudo firefox"? DON'T DO THIS. If you did, then see **Solution** [*[COLOR="Red"]**FOT001**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT001).

---

### Post by Johnny B on 2009-07-23
are you using any firefox addons that deal with your bookmarks?
xmarks?


edit:
if you want to delete all your bookmarks:
mv $HOME/.mozilla/firefox/*.default/bookmarks.html $HOME/.mozilla/firefox/*.default/bookmarkbackups

---

### Post by lovinglinux on 2009-07-23
> **Johnny B said:**
> edit:
if you want to delete all your bookmarks:
mv $HOME/.mozilla/firefox/*.default/bookmarks.html $HOME/.mozilla/firefox/*.default/bookmarkbackups

That's not correct. Since Firefox 3 this file only holds the default bookmarks shipped with the application, that are imported to the database when a new profile is created. The user bookmarks are stored in the database file *places.sqlite* and the backups are the json files under ~/.mozilla/firefox/*/bookmarkbackups

---

