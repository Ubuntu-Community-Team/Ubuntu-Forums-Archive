---
title: "Help! History of Gnome Popup Notifications?"
date: 2011-01-30
forum: General Help
---

### Post by br4nd0nh347 on 2011-01-30
I've been searching google for a long time and now I leave it up to you.

I recently had a popup bubble in ubuntu come up and it may have been one of the disturbing nature.   (no images, just the content of what it said may have been cause of concern)

The thing is is that it went away before I could even read it really.  I've been searching for a long time (embarrassed to say how long) for anything related to viewing previous popup notifications that come up in ubuntu. (like a history)

I've checked the logs and they are fine, I do not see any gnome notifications in them though.

Is there any way to see previous gnome popups?

---

### Post by DanCar on 2011-02-04
I have the same issue.

Thanks for any pointers,
Daniel

---

### Post by DanCar on 2011-02-04
ok googled and found out the answer.  In a terminal window type:
cat ~/.cache/notify-osd.log

:)

---

### Post by furiat on 2011-02-15
I have found something you need, applet called "recent-notifications" there is even PPA:

[http://www.webupd8.org/2011/02/never-miss-notifyosd-notification-with.html](http://www.webupd8.org/2011/02/never-miss-notifyosd-notification-with.html)

It is not perfect, but it works.

---

### Post by br4nd0nh347 on 2011-02-15
> **furiat said:**
> I have found something you need, applet called "recent-notifications" there is even PPA:

[http://www.webupd8.org/2011/02/never-miss-notifyosd-notification-with.html](http://www.webupd8.org/2011/02/never-miss-notifyosd-notification-with.html)

It is not perfect, but it works.

Thanks for your help, and reply to this.

---

