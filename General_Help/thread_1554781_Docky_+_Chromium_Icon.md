---
title: "Docky + Chromium Icon"
date: 2010-08-17
forum: General Help
---

### Post by mexicanseaf00d on 2010-08-17
Hi all,

I played around with chromium-browser and somehow I managed to change the Icon in Docky to this:

[img]http://666kb.com/i/blvelxf6177i2dsvh.jpg[/img]

I wanted to 'iconize' the forum-tab, but I used the wrong menu entry and it actually added an application shortcut to gnome-main menu and desktop

Does anyone have an idea how to change it back in Docky? Every other menu shows the normal Icon for chromium.

It's no big deal, but I bet it's simple and i just cant figure it out :rolleyes:

---

### Post by Sorcix on 2010-09-05
I'm having the same issue. Docky shows the gmail icon for chromium after trying to save a shortcut to gmail. Tried removing the docky config folders and reinstalling but it didn't help.

---

### Post by mexicanseaf00d on 2010-09-05
I removed the app-shortcut for that 'pinned' tab from the main menu - I am not sure if this was the cause, but after a while i noticed that the normal chrome icon was back!

---

### Post by Matthileo on 2010-10-26
I removed the menu shortcut but I'm still having the same issue.

---

### Post by tas.b on 2010-11-05
You may want to try "How to Customize Window Matching" from the Docky wiki
[http://wiki.go-docky.com/index.php?title=How_to_Customize_Window_Matching](http://wiki.go-docky.com/index.php?title=How_to_Customize_Window_Matching)

---

### Post by kellymartinv on 2010-11-19
Actually, the reason is because even after you delete that darn gmail shortcut, it's still hidden on your system. For some reason Docky reads that shortcut instead if Chromium.  I deleted the chrome*gmail.desktop file in ~/.local/share/applications and it took care of my issue with it.

(If that doesn't work, I found another copy of that .desktop file in ~/.gnome/apps too, which I also deleted).

---

### Post by ska08 on 2011-04-22
So glad I found this post! I've been stuck with the last pass icon representing chrome since december.  Fixed now!  Thanks!

---

