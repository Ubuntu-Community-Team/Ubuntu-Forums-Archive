---
title: "What Does This Mean?"
date: 2010-11-20
forum: General Help
---

### Post by jazzabrotha on 2010-11-20
I tried to  open update manager through terminal and I got:

update-manager
terrance@terrance-desktop:~$ update-manager
/usr/bin/update-manager:104: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  app = UpdateManager(data_dir, options)
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:1075: Warning: g_object_notify: object class `PangoLayout' has no property named `width'
  gtk.main_iteration()
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:1075: GtkWarning: IA__gtk_widget_size_allocate: assertion `GTK_IS_WIDGET (widget)' failed
  gtk.main_iteration()
Segmentation fault
terrance@terrance-desktop:~$ update-manager

What exactly does this mean? what needs to be fixed? if so, how?
Im running a Compaq Evo desktop with Maverick 10.04

Thanks alot!

---

### Post by hakermania on 2010-11-20
This is quite weird! This messages appear when you are trying to open a program as root. For instance if you try to open nautilus being root from a terminal you'll get errors like this. Can you open update-manager from the ubuntu menu? (System->Administator->Update Manager)

---

### Post by jazzabrotha on 2010-11-20
Well when I try to open software center from the menu, It won't open, which was the reason why I tried It from prompt

---

### Post by cchhrriiss121212 on 2010-11-20
Try running this from a terminal:
gksudo synaptic
Then reload and mark all upgrades.

---

