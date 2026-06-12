---
title: "Strange exception"
date: 2006-04-13
forum: General Help
---

### Post by 3david on 2006-04-13
Hi, i've installed ubuntu 5.10 two days ago, i then installed almost everything in the Automatix script, i've been working with it for the past two days,

at first, i got this error with Listen, now i'm also getting it with gnome-terminal,
i can open one gnome-terminal, i get this warning message, but it opens,
if i try to open another gnome-terminal but it won't open, it doesn't write anything

```

(gnome-terminal:27161): Bonobo-Activation-WARNING **: Strange exception (IDL:omg.org/CORBA/COMM_FAILURE:1.0) from active server registration
Error registering terminal with the activation service; factory mode disabled.

(gnome-terminal:27161): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:27161): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

```

if I kill the bonobo-activation-server, and then run gnome-terminal again, it works, i can open as many windows as i want. but i still get the two Gtk-CRITICAL error messages.

any ideas?

---

### Post by dannemil on 2006-04-26
[QUOTE=3david]Hi, i've installed ubuntu 5.10 two days ago, i then installed almost everything in the Automatix script, i've been working with it for the past two days,

at first, i got this error with Listen, now i'm also getting it with gnome-terminal,
i can open one gnome-terminal, i get this warning message, but it opens,
if i try to open another gnome-terminal but it won't open, it doesn't write anything

```

(gnome-terminal:27161): Bonobo-Activation-WARNING **: Strange exception (IDL:omg.org/CORBA/COMM_FAILURE:1.0) from active server registration
Error registering terminal with the activation service; factory mode disabled.

(gnome-terminal:27161): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:27161): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

```

if I kill the bonobo-activation-server, and then run gnome-terminal again, it works, i can open as many windows as i want. but i still get the two Gtk-CRITICAL error messages.

any ideas?[/QUOTE]


I am getting exactly this error. What's even worse is that when I try to open a root terminal, it will eventually open, but no prompt appears in the terminal.

I haven't been able to solve this problem.

---

