---
title: "Shutting down ubuntu"
date: 2010-11-20
forum: General Help
---

### Post by waltwin on 2010-11-20
When shutting down or restarting  ubuntu 10.10 I get a second window asking if I want to do what I am asking. How do I eliminate this second window.

Thank you for the help

waltwin

---

### Post by 3rdalbum on 2010-11-20
Hit Alt-F2 and type:

```
gconf-editor
```

Look through the tree on the left: /apps/indicator-session

Then put a tick in the "suppress_logout_restart_shutdown" box in the right-hand pane.

I'd still recommend leaving it as the default (to prompt) because occasionally you will go to the Shut Down menu item and then immediately think "Oh... I wish I hadn't done that". Yes, even experienced Ubuntu users do this :-)

---

### Post by waltwin on 2010-11-20
Thank you for the response. I will consider your thought before I make any changes. It's nice to know how, just in case. I can always undue the change.

waltwin

---

