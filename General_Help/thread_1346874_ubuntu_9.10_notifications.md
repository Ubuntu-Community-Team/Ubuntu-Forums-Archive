---
title: "ubuntu 9.10 notifications"
date: 2009-12-05
forum: General Help
---

### Post by Strongman332 on 2009-12-05
has any one been able to move the notifications to the bottom right yet.

also i can fall back to the old notification system like the one 8.04

---

### Post by Strongman332 on 2009-12-29
bump

---

### Post by QIII on 2009-12-29
Not at my Ubuntu machines right now, but...

Assuming you are using Gnome:

I think that Alt-F2 still gives you the Run Application box.

Type "gconf-editor" (no quotes) and click Run.

When the Config Editor opens, click Apps and find update-notifier and click it.

There should be a box called "auto-launch" or similar.  Uncheck it.

You should be back to the notifier in the panel instead of getting the pop-up when you are in the middle of something.

---

### Post by Strongman332 on 2009-12-29
oh I have already done that for the updates but I am talking about the  notifications like volume and brightness. the ones that show up at the top of the screen

---

