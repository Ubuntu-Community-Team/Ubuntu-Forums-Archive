---
title: "thunderbird launcher icon missing"
date: 2011-07-11
forum: General Help
---

### Post by webcomm on 2011-07-11
I've been using natty for a few weeks.  I can't remember how to add something to the launcher, other than dragging it.  I had thunderbird in the launcher, but accidentally removed it.  Now, when I drag it back to the launcher, it's there in the launcher, but as a blank space.  The thunderbird icon is missing.  I can click on the blank space to launch it, but would like to add the icon.

ubuntu 11.04

---

### Post by seawolf167 on 2011-07-12
If you remove and re-add it from gconf-editor do you still have the same issue?

```
[ALT][F2] gconf-editor
```

browse to / -> desktop -> unity-2d -> launcher -> right-click and select to edit key of "favorites"

remove your thunderbird entry and add

```
thunderbird.desktop
```

then logout and logback in, see if the icon appears

---

### Post by webcomm on 2011-07-12
thanks for your reply.  The thunderbird icon appeared in the launcher after I rebooted, so I didn't have to try your suggestions.

---

### Post by seawolf167 on 2011-07-12
Glad it worked nice and easily! Please mark this thread as solved under thread tools.

---

### Post by RichardCain on 2011-07-18
I had the same problem after installing Thunderbird 5.0 beta.  Same thing - a simple reboot solved the problem.
Incidentally, no Unity items appear under Desktop on gconfig-editor.  Any suggestions?

---

