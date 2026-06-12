---
title: "keyring does not unlock after booting"
date: 2012-01-17
forum: General Help
---

### Post by D0Z on 2012-01-17
This is quite annoying. After restarting my computer is have to manual enter all usernames and passwords again.
After entering those the keyring unlocker appears saying it didn't unlock after booting.

I enter my password and press ok, but when rebooting it all starts over.

Is there an (easy) fix for this issue? I'm using Xubuntu 11.10.

---

### Post by cottfcfan on 2012-01-17
There is an easy fix, I used it but can't find it now.
Copy & paste the message you get into Google, I found the answer quite quickly that way. It involves deleting some file in your Home folder.

---

### Post by cottfcfan on 2012-01-17
The files you need to delete are in home /.gnome2/keyrings.
I think its safe to delete both those files (login.keyring & user.keystore) & reboot. You may have to set your login password again, but your problem should be resolved.

---

### Post by D0Z on 2012-01-17
That solved the problem, many thanks.

---

### Post by D0Z on 2012-01-18
I just found out the problem has returned! After fixing it yesterday it remained fine after rebooting.

---

### Post by D0Z on 2012-01-20
It just doesn't remember any of my passwords after rebooting.
Is there another wat to fix this?

---

### Post by cottfcfan on 2012-01-21
Sorry its the only way I know to solve the problem.
Works fine for me.
Maybe someone else can help.

---

