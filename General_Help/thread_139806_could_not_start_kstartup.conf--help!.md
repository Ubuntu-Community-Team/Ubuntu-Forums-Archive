---
title: "could not start kstartup.conf--help!"
date: 2006-03-04
forum: General Help
---

### Post by joey111 on 2006-03-04
hi, does anybody have an idea? i tried to do a parallel fedora core 4 installation and use my kubuntu 5.10 home/user directory as my fedora home directory. but when i try to login to kubuntu again it says could not start kstartupconfig and i am back at the login screen; when i try to login to fedora it says now "/etc/x11/gdm/Presession/Default..could not create gnome accelerators could not write to directory /home/user/.gnome2/accels". permisson denied..but i can write if i login as failsafe.. thx
chown user.user /home/user/.gnome2/accels doesn't help..

---

### Post by devnulljp on 2006-07-18
Try changing the ownership of everything in .kde to your username and group.
I guess you can't get into kde at all? So, cntl-Alt-F1 should dump you into a separate terminal. Log in as yourself or some other user with sudo privileges.

From the parent folder of your username, type:
```
sudo chown -R <username>:<usergroup> .kde
```

Restart X, and that should fix it for you...

---

### Post by andril on 2006-10-23
Thanks you saved my day :KS

---

