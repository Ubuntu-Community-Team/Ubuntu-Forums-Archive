---
title: "amarok crashes"
date: 2010-03-07
forum: General Help
---

### Post by wirate on 2010-03-07
I've recently been using amarok and liked it a lot. I unchecked the show system tray in configuration, restarted amarok and then checked it again. Now amarok crashes whenever I go into configuration or browse through local files. I have tried reinstalling and deleting the directory ~/.kde/share/apps but no use.
any help?

---

### Post by wirate on 2010-03-07
this is strange. when I start amarok with any other widget style, it works fine. but it doesnt like bespin. when run with the bespin style, the following messages appear in the terminal

```
QWidget::setMinimumSize: (Browsers dock/QDockWidget) Negative sizes (100,-1) are not possible
Object::connect: No such signal Playlist::GroupingProxy::activeRowChanged( int )
Object::connect:  (sender name:   'GroupingProxy')
Object::connect: No such signal Playlist::GroupingProxy::activeRowChanged( int )
Object::connect:  (sender name:   'GroupingProxy')
QWidget::setMinimumSize: (Playlist dock/QDockWidget) Negative sizes (257,-1) are not possible
KCrash: Application 'amarok' crashing...
sock_file=/home/user/.kde/socket-ubuntu/kdeinit4__0

```

---

