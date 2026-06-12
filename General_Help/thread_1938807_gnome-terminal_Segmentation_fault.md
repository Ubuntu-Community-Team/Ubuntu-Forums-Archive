---
title: "gnome-terminal Segmentation fault"
date: 2012-03-10
forum: General Help
---

### Post by sonriente on 2012-03-10
Hello!

For some reason when I'm trying to open a new tab in gnome-terminal it crashes with the 'Segmentation fault' error message.
I've tried to debug it and found the following:

```
>gdb gnome-terminal
(gdb) set args ~/.bashrc
(gdb) run
Starting program: /usr/bin/gnome-terminal ~/.bashrc
[Thread debugging using libthread_db enabled]

(gnome-terminal:4738): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:77:18: 'inherit' is not a valid color name

(gnome-terminal:4738): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:225:20: Junk at end of value

(gnome-terminal:4738): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:531:20: Junk at end of value

......

Program received signal SIGSEGV, Segmentation fault.
0x0122ac23 in _gtk_css_number_get ()
   from /usr/lib/gtk-3.0/3.0.0/theming-engines/libunico.so
```

The problem could not be reproduced when I'm using a simple theme like HighContrast (HighContrast invesrse).

I guess the problem arose after I had tried to install gimp 2.7.x from untrusted ppa. (gimp had failed to install, but I suspect glib was upgraded).

system: ubuntu 11.10 i386.

Please help me to fix the issue.
Thanks in advance.

---

