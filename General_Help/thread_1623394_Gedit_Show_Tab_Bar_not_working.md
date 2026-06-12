---
title: "Gedit Show Tab Bar not working"
date: 2010-11-16
forum: General Help
---

### Post by Cronos89 on 2010-11-16
I've been with this problem for ages and finally decided to post.

Installed the gedit-plugins package (*Version: 2.30.0-1ubuntu1*).

After enabling **Show/Hide Tabbar** plugin, and unckecking View-> Tabbar, tabs are still there, anyone knows what may be happening?

I'm currently running Ubuntu 10.10 amd64, with *gedit version 2.30.3*

---

### Post by wojox on 2010-11-16
Try rebooting. Mine works fine here. Although I'm using 10.04.

---

### Post by Ancanus on 2010-11-16
I tried to reproduce your issue, but the tabs do disappear for me.

Does running gedit from the terminal produce any valuable outputs when you perform your routine?

```

~$ apt-cache policy gedit
gedit:
  Installed: 2.30.3-1ubuntu1
  Candidate: 2.30.3-1ubuntu1
  Version table:
 *** 2.30.3-1ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ maverick/main i386 Packages
        100 /var/lib/dpkg/status

gedit-plugins:
  Installed: 2.30.0-1ubuntu1
  Candidate: 2.30.0-1ubuntu1
  Version table:
 *** 2.30.0-1ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ maverick/universe i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Cronos89 on 2010-11-16
Now that you mention it...

~$gedit
```
2010-11-16 19:22:05,687 DEBUG resources - Initializing resource locating
2010-11-16 19:22:05,758 DEBUG Preferences - <value key='BibtexExtensions'> not found
2010-11-16 19:22:05,773 DEBUG JobManager - Created JobManager instance 28411728
2010-11-16 19:22:05,777 DEBUG GeditLaTeXPlugin - activate
2010-11-16 19:22:05,777 DEBUG WindowContext - init
2010-11-16 19:22:05,849 DEBUG GeditWindowDecorator - _init_tab_decorators: initialized 0 decorators
[B]sys:1: Warning: invalid cast from `GtkButton' to `GtkNotebook'
sys:1: GtkWarning: IA__gtk_notebook_set_show_tabs: assertion `GTK_IS_NOTEBOOK (notebook)' failed[/B]
2010-11-16 19:22:06,123 DEBUG GeditWindowDecorator - active_tab_changed
2010-11-16 19:22:06,124 DEBUG GeditWindowDecorator - ---------- ADJUST: None
2010-11-16 19:22:06,126 DEBUG GeditWindowDecorator - No window-scope views for this extension
2010-11-16 19:22:06,126 DEBUG GeditWindowDecorator - _set_selected_bottom_view: 2
2010-11-16 19:22:06,126 DEBUG GeditWindowDecorator - _set_selected_side_view: 3
2010-11-16 19:22:06,135 DEBUG GeditWindowDecorator - tab_added

```

and following your...
```

apt-cache policy gedit
gedit:
  Installed: 2.30.3-1ubuntu1
  Candidate: 2.30.3-1ubuntu1
  Version table:
 *** 2.30.3-1ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ maverick/main amd64 Packages
        100 /var/lib/dpkg/status

gedit-plugins:
  Installed: 2.30.0-1
  Candidate: 2.30.0-1ubuntu1
  Version table:
     2.30.0-1ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ maverick/universe amd64 Packages
 *** 2.30.0-1 0
        100 /var/lib/dpkg/status

```

---

### Post by Ancanus on 2010-11-16
It seems to me that your current GTK+ installation is not compatible with the one gedit expects. Are you maintaining your own version?

```

$ apt-cache policy libgtk2.0-0
libgtk2.0-0:
  Installed: 2.22.0-0ubuntu1
  Candidate: 2.22.0-0ubuntu1
  Version table:
 *** 2.22.0-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ maverick/main i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Cronos89 on 2010-11-16
Nope, in fact, i did a clean ubuntu install last night.
 ```
~$ apt-cache policy libgtk2.0.0
libgtk2.0-0:
  Installed: 2.22.0-0ubuntu1
  Candidate: 2.22.0-0ubuntu1
  Version table:
 *** 2.22.0-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ maverick/main amd64 Packages
        100 /var/lib/dpkg/status
libgtk2.0-0-dbg:
  Installed: (none)
  Candidate: 2.22.0-0ubuntu1
  Version table:
     2.22.0-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ maverick/main amd64 Packages

```

---

### Post by Cronos89 on 2010-11-16
Tried disabling all of the plugins and enabled only the Show/Hide Tabbar and it works. so its a plugin problem.

Will enable 1 by one till i find the problematic one.

EDIT: Oh damn, the Gedit LaTeX Plugin is the one that's messing with everything :(

Thnx Ancanus for your time :D

---

