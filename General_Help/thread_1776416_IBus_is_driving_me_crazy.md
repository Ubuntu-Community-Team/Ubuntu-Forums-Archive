---
title: "IBus is driving me crazy"
date: 2011-06-06
forum: General Help
---

### Post by vickycq on 2011-06-06
IBus always gives me a lot of trouble when i've finished reinstalling my system, 
i cant use it in any application. Instead, it just shows "No input window" in systray.       

 i have searched at Google for various methods such as editing .profile , .bashrc , and /usr/lib/gtk-2.0/2.10.0/immodule-files.d/libgtk2.0-0.immodules.    Also i've tried configuring im-config. 

run           ```
$ echo $XMODIFIERS:$GTK_IM_MODULE:$QT_IM_MODULE
``` 
returns        ```
@im=ibus:ibus:ibus
```

Also, when i run applications in terminal in order to get error messages, it shows something like:
```
(gedit:1844): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so) initialization check failed: GLib version too old (micro mismatch)

(gedit:1844): Gtk-WARNING **: Loading IM context type 'ibus' failed
```

System is Linux Mint Debian.

i'm getting tired of this...Any idea about what the problem is ?

Thanks in advance.

---

