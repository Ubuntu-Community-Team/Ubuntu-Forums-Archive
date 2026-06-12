---
title: "Removed Shutdown and Instant Messaging Status From Panel"
date: 2010-12-07
forum: General Help
---

### Post by Clarkie08 on 2010-12-07
Hey there,

I booted up my laptop as usual and found that when I opened Empathy IM Client it would not allow me to login when I changed the status to Online (or equivalent). Normally as soon as I open the client the Messaging Status can be changed in the top right next to the clock so I tried to remove it but unfortunately it took the shut down panel with it.

To try and bring them back I used the restore panel commands in terminal:

```
$ gconftool-2 --shutdown
$ rm -rf ~/.gconf/apps/panel
$ pkill gnome-panel
```Unfortunately the panels all reloaded, but without any change.

1. How can I restore the shut down and messaging section to the top panel (as is in the default)?
2. How can I get instant messaging to work again?

Thanks for your help,
Clarkie

PS. I'm a Ubuntu noob, only installed it about 2 days ago. Thus I may need some very basic instructions to anything complicated.



EDIT:
I just found the panel section was called the Indicator Applet, but now it's in the wrong place...

---

### Post by germanix on 2010-12-07
A right click on the "indicator applet" should open a drop down menu. If "lock to panel" is set, a left click on "lock to panel" will free it. Then left click on "move". Then move your mouse cursor to the place in the panel where you want the applet to be and left click. The applet will move to that position. (you can also drag it there) Once in place right click the applet again and choose "lock to panel" from the drop down menu.
I do not use this applet myself so cannot help you with the other problem but someone will surely do so. Just be patient.

---

### Post by Clarkie08 on 2010-12-07
Thanks for that, it helped me get the applets and pannels sorted in the right place :) now let's see about the instant messaging...

Solved by reactivating all the accounts :) thanks for the help germanix!

---

### Post by germanix on 2010-12-07
Glad I could help, and welcome to the forum.

---

