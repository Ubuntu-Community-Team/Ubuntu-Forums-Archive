---
title: "Wierd crash in application"
date: 2012-01-01
forum: General Help
---

### Post by iamgeniusrnti on 2012-01-01
Got a crash issue with an app.  I don't know much about this app but it was bought for my wife a while ago.  It appears to be a calendar app driven by Flash.  It starts up ok but when you click a button, it switches to full screen mode and then crashes.  There is no evidence of said crash in any of the kernel logs or sys log, that I can see.  But here is the console output.

Any help here?

```

samantha@Samantha-pc:/opt/Jacquie Lawson London Advent Calendar/bin$ ./Jacquie\ Lawson\ London\ Advent\ Calendar 

(Jacquie Lawson London Advent Calendar:356): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(Jacquie Lawson London Advent Calendar:356): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(Jacquie Lawson London Advent Calendar:356): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(Jacquie Lawson London Advent Calendar:356): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(Jacquie Lawson London Advent Calendar:356): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(Jacquie Lawson London Advent Calendar:356): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(Jacquie Lawson London Advent Calendar:356): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(Jacquie Lawson London Advent Calendar:356): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(Jacquie Lawson London Advent Calendar:356): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

samantha@Samantha-pc:/opt/Jacquie Lawson London Advent Calendar/bin$ 

```

---

### Post by syerges on 2012-01-01
You've installed the wrong version of the program. If you are running 32 bit processor you need 32 bit software, not 64 bit.

---

### Post by iamgeniusrnti on 2012-01-01
Cool.  Thanks.  My wife actually installed it when I was on a trip.  They probably don't make a 32 bit version.  Thanks again for your input though.  Happy New Year!

---

### Post by syerges on 2012-01-01
no problem. Happy New Year to you as well!

---

