---
title: "Delete Hybernate Option"
date: 2006-06-11
forum: General Help
---

### Post by dacky on 2006-06-11
I am running Ubuntu 6.06 with ltsp.  When the workstations log out, they have the option of "hybernate."  When this is selected, it shuts down the whole server.  How can I delete this option for the clients?  I actually do not need it at all for the server either.

---

### Post by Rui Pais on 2006-06-11
hi,
if you want to do it in a per-user basis
you can run gconf-editor and uncheck the keys 'can_hibernate' and 'can_suspend' on /apps/gnome-manager.

On global basis (to all users) the only solution i found was:
edit /etc/default/acpi-support and set
ACPI_SLEEP=false
ACPI_HIBERNATE=false
*edit:*Note that  this will not make Hybernate/Suspend buttons disappear, only make them unuseful.

and if that fails the brute mode that some people use is,
make /etc/acpi/sleep.sh and /etc/acpi/hibernate.sh not executable.

hth

---

### Post by kihai on 2006-07-17
Or (this is how I did it) you can make a default user account, logging in to it, change all settings, shortcuts, menues you'd like your users to see and then go to System-Settings-Sessions. There you can unclick "ask while logging off" (don't know how it says correctly, I'm using a German version).
Then you log off, and copy the contents of the default user directory to /etc/skel (Don't forget hidden files and when you find a file "session" in .gnome2 directory, delete it). This is rather a quick and dirty workaround but it was the best solution I could find...

---

