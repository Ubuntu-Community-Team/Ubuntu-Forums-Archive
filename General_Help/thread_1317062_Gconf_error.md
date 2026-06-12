---
title: "Gconf error?"
date: 2009-11-06
forum: General Help
---

### Post by hwttdz on 2009-11-06
I get the following error when trying to open up gedit through an ssh connection.

GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-OtBtdUTtpt: Connection refused)

Any suggestions?

---

### Post by pjbgravely on 2009-11-06
It sounds like an error where the gconf of each machine are not connecting.

Do you have x forwarding enabled? 

For a work around use pico.

Paul

---

### Post by hwttdz on 2009-11-06
I was working through x-forwarding.  Never tried pico, my non-graphical editor of choice is nano.

---

### Post by hwttdz on 2009-11-10
I think it may be due to another user, physically at the computer, logging in graphically?  Or at least the problem seemed to pop up as soon as someone logged in. A workaround is to have the person who logged in logout and log in again.  I don't know how that helps but...

If I "gedit test.txt" I get the error, but if I "sudo gedit test.txt", I don't get the error.  Hmm.

---

### Post by pjbgravely on 2009-11-10
It could be a messed up .gconf file. Try logging in, renaming it, logging out and back in. This might be bad to do if someone else is currently logged in to that user so make sure it is clear with the users command, you should only see one of that user name.

Paul

---

