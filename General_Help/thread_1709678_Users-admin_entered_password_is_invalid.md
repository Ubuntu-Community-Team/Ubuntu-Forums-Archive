---
title: "Users-admin: entered password is invalid"
date: 2011-03-18
forum: General Help
---

### Post by Domtche on 2011-03-18
Hi,

I'm running on ubuntu 10.04 lts, and i'm trying to launch the users-admin window, either from the menu as from the terminal, but always get the message:

The entered password is invalid

And then it closes down on me. 

when i sudo or even change into root, it still tells me the password is invalid. Weird thing is, I can perfectly well sudo other commands but not users-admin and not network-admin (same problem). Both give an error on GLib-GObject-CRITICAL, but i guess that's not what's hampering me.

domtche@####:~$ sudo users-admin
[sudo] password for domtche: 
(users-admin:6166): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
ers-admin:6166): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

I think i've got all proper groups assigned to my user:

domtche@#####:~$ groups
domtche adm dialout cdrom plugdev lpadmin netdev admin sambashare

I have already remove and reinstalled the 'xubuntu-system-tools' package using synaptic, but to no avail.

There is only one account on my linux, and have sudo'ed lots before, so why would it not work here?

---

