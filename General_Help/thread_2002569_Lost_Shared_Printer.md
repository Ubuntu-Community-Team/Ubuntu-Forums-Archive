---
title: "Lost Shared Printer"
date: 2012-06-12
forum: General Help
---

### Post by feartheterrapin on 2012-06-12
Never had a problem with sharing a printer between two 10.04 installations.  I recently installed 12.04 on the PC with the attached printer.  The shared printer worked for about one day.  Now when trying to print from the remote PC I get the following authentication message:
[[IMG]http://img341.imageshack.us/img341/7126/screenshotjr.png[/IMG]]("http://imageshack.us/photo/my-images/341/screenshotjr.png/")
None of the user passwords including the sudo password work.  Printer works fine from the PC it is connected to.  What can I try?

---

### Post by drdos2006 on 2012-06-12
See if you can administrate the printer using your browser to connect using port 631 with :  http://<the-IP-address>:631

regards

---

### Post by feartheterrapin on 2012-06-12
I can connect.  But when I click on the Administer link, I get Forbidden.

---

### Post by drdos2006 on 2012-06-13
Sounds like something has not installed properly.
Try removing and re-installing CUPS.

regards

---

### Post by feartheterrapin on 2012-06-18
Once I checked remote administration,  http://<the-IP-address>:631 worked from remote machine.  All settings look correct.   Still have same problem.  Error log attached.

One question, when using  http://<the-IP-address>:631, there is a box for specific share users.  Using "system-config-printer", there is a box to check allow all users except, which is checked.  Is there a difference between the settings in both configs?

Also, any chance removing Unity and adding Gnome has caused these problems?

---

### Post by feartheterrapin on 2012-06-19
Moved printer over to a Ubuntu 10.04 install.  Works great.  Wish there was a way to to share a printer from 12.04.  It almost seems there are too many avenues to control the printer from 12.04.  Maybe I don't understand, but it seems Unity, Gnome, and the OS want to have control of the settings.

---

