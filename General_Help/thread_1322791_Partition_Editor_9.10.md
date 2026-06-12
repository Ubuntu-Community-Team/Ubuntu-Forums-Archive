---
title: "Partition Editor 9.10"
date: 2009-11-11
forum: General Help
---

### Post by texas.chef94 on 2009-11-11
After installing partition editor (gparted) from synaptic I usually find it in system+admisistration, but have looked and found nothing. I kind like it on my desktop so please advise and as always thanks

---

### Post by fooman on 2009-11-11
i think it used to be called partition editor in the menu...

it is now just "gparted"....system > administration > gparted

---

### Post by texas.chef94 on 2009-11-11
> **fooman said:**
> i think it used to be called partition editor in the menu...

it is now just "gparted"....system > administration > gparted

You are so right, but it still does not appear under my system+administration and package manager shows it green and loaded

---

### Post by fooman on 2009-11-11
you can add it if it is not there...

right-click on "applications - places - system" in the top panel and choose "edit menus" from the drop-down list.

when the main menu opens,  scroll down in the left column and click once on "administration".  then look on the right side and see if "gparted" is listed.  if it is...put a check mark next to it.  close the main menu window and it should now be listed in the menu.

it it was not listed under administration....then in the right column click "new item".  in the "create launcher" window,  type "gparted" in the name space (no quotes).  then in the command space,  type or copy/paste the following:

```
gksu /usr/sbin/gparted
```

click close and gparted should be in the menu under system > administration.

hope that helps.

---

### Post by kestrel1 on 2009-11-11
Did you logout after installing it, sometimes things only appear after a logout/ login.

---

