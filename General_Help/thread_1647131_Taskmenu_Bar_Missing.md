---
title: "Task/menu Bar Missing"
date: 2010-12-16
forum: General Help
---

### Post by quietguy83 on 2010-12-16
First off late me state that i know nothing about ubuntu and i am try to help someone(my father) who knows even less lol. Last night the 13yr old little girl got on his computer and was playing around now the Task/Menu bar is gone and he doesnt know how to get it back.... or do anything else without it. ive told him that this is probably just a simple setting but im not there to play with his computer to figure ubuntu out for him thus im forced to seek wisdom here. I need idoit lvl instructions on how to reenable this bar can anyone help?

---

### Post by Frogs Hair on 2010-12-16
Hi,

To add the task bar right click at the top of the screen and select new panel , then right click the panel and select add to panel . From the menu add the items you will need . Window list , Menu , Clock , Session Applet , Indicator Applet , Notification Area , and anything else you would like.

---

### Post by wojox on 2010-12-16
Try this. Open a terminal and run theses two commands:


```
gconftool --recursive-unset /apps/panel
pkill gnome-panel
```

---

### Post by trinitydan on 2010-12-16
Try this:

[http://albertsiow.wordpress.com/2008/06/26/restore-panel-bartop-in-ubuntu-gnome/](http://albertsiow.wordpress.com/2008/06/26/restore-panel-bartop-in-ubuntu-gnome/)

---

### Post by hanscholtes on 2011-04-15
> **wojox said:**
> Try this. Open a terminal and run theses two commands:


```
gconftool --recursive-unset /apps/panel
pkill gnome-panel
```

Thanks Wojox!
It did the trick for me!

---

