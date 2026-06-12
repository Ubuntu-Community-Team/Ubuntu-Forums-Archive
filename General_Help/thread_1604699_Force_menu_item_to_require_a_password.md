---
title: "Force menu item to require a password"
date: 2010-10-24
forum: General Help
---

### Post by glue on 2010-10-24
I only want someone with root privileges to be able to run a particular app from a menu. Adding sudo to the beginning of the command textbox doesn't seem to work though using sudo on the command line works fine. How do I force a password for a menu item?

---

### Post by SavageWolf on 2010-10-24
Try gksudo, it creates a visual prompt, rather they a text one, which would fail.

---

### Post by krishnandu.sarkar on 2010-10-24
Well...the programs in the menu item are intended to run by everyone. I think you should keep your programs to /sbin if you want to run them only by admins.

---

### Post by egalvan on 2010-10-24
> **krishnandu.sarkar said:**
> Well...the programs in the menu item are intended to run by everyone. I think you should keep your programs to /sbin if you want to run them only by admins.

Mnay items in the menu system are intended to be run under root...ç
Systenm Utilities,  Adminstration, etc.

And where the executable is located has no bearing on the menu.

While changing the menu system to require root, a far more secure methond is to change the ownership of the app itself to root, and make sure only root has privalages (read, write, execute).

Otherwise a (mildly) savy user can edit the menu item, or drop to a shell (command line).

---

### Post by krishnandu.sarkar on 2010-10-24
> **egalvan said:**
> Mnay items in the menu system are intended to be run under root...ç
Systenm Utilities,  Adminstration, etc.

And where the executable is located has no bearing on the menu.

While changing the menu system to require root, a far more secure methond is to change the ownership of the app itself to root, and make sure only root has privalages (read, write, execute).

Otherwise a (mildly) savy user can edit the menu item, or drop to a shell (command line).

Thanks for correcting me :)

---

### Post by glue on 2010-10-24
> **SavageWolf said:**
> Try gksudo, it creates a visual prompt, rather they a text one, which would fail.

D'Oh. I should've guessed this. LOL.

---

### Post by deserthowler on 2010-10-24
when you get into edit menus, look at properties for synaptic.  It should show you how to call the program using gksudo.

Earl

---

### Post by perspectoff on 2010-10-24
> **SavageWolf said:**
> Try gksudo, it creates a visual prompt, rather they a text one, which would fail.

Right. Or kdesu for KDE (Kubuntu).

So a menu item for a program that should be run with sudo root privileges (i.e. as the root user temporarily) should have as the command line, for example:

 gksudo nautilus

which would start the Nautilus file browser as the root user, presenting a password dialogue prior to launching Nautilus.

In Kubuntu (KDE), a similar thing would be achieved:

 kdesu dolphin

This can be used for any app, so that any app can be started as the root user instead of as a regular user.

If you want to restrict an app to be used by only the root user, you must change the permissions of the app so that the owner of the app is only root and the execute permission only applies to root.

If you have a group of users to whom execution is restricted, of course, you must specify that group for the app and then allow execution only by users in that group.

That is a separate step from using gksudo or kdesu, of course.

---

