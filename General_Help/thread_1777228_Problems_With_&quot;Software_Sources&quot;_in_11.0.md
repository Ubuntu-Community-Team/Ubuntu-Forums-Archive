---
title: "Problems With &quot;Software Sources&quot; in 11.04"
date: 2011-06-07
forum: General Help
---

### Post by anonymousdude on 2011-06-07
So I noticed Software Sources was missing from my menu in 11.04.  I found an explanation for how to add it to my menu at the following page:

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

However, after following the instructions it was still missing so I tried to run it from the command line.  The command 'software-properties-gtk' opened a notification window that read "You need to be root to run this program."  

So my first question is.. is the fact that it needs to be run with root privileges the reason it's not appearing in my application menu and if so how can I fix that?

So then I tried running the command again with sudo and it opened the program, however, it also gave me the following warnings in the terminal window:

WARNING: can not get name for '<CellRendererText object at 0x9241f7c (GtkCellRendererText at 0x8e893b0)>'
WARNING: can not get name for '<TextBuffer object at 0x924534c (GtkTextBuffer at 0x8e85950)>'

Should I be considered about these?

---

### Post by TeoBigusGeekus on 2011-06-07
> **anonymousdude said:**
> So my first question is.. is the fact that it needs to be run with root privileges the reason it's not appearing in my application menu and if so how can I fix that?
The command needs to be run with root privileges because it changes essential part of your system - it has nothing to do with not appearing in your app menu.
By the way, it shouldn't be in your app menu; it should be in your System->Administration menu.
You could right click your menus->edit menus and add a new launcher for it with this command
```
gkus software-properties-gtk
```

> **anonymousdude said:**
> So then I tried running the command again with sudo and it opened the program...
Don't use sudo for gui apps; use gksu (or gksudo) instead. 
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

> **anonymousdude said:**
> 
however, it also gave me the following warnings in the terminal window:

WARNING: can not get name for '<CellRendererText object at 0x9241f7c (GtkCellRendererText at 0x8e893b0)>'
WARNING: can not get name for '<TextBuffer object at 0x924534c (GtkTextBuffer at 0x8e85950)>'

Should I be considered about these?

No. Probably an inconsistency of your gtk theme. Ignore the messages completely.

---

### Post by anonymousdude on 2011-06-07
Good stuff.  Thanks for all the info.

---

