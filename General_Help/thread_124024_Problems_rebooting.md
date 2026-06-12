---
title: "Problems rebooting"
date: 2006-01-31
forum: General Help
---

### Post by jadugarr on 2006-01-31
Recently ever time I try to reboot in breezy I get this annoying message after X is killed.  It says: "Give root password for maintence or type Control-D to continue".  Now hitting control-d doesn't do anything, so I have to enter my root password (the actual root, not sudo user) and give the reboot command manually.  I'm not sure what I changed that caused this, I tweak things a lot and reboot very seldom, so it could have been something I changed over a week ago.

Has anyone experience problem and/or know how to solve it?

---

### Post by gamma on 2006-02-01
The only time I've gotten that message was at boot when it failed to mount a partition critical to the kernel booting. Is everything unmounting successfully? Did you check the kernel logs?

---

### Post by z-vet on 2006-02-01
I use 
```
sudo shutdown -r now
```
as a workaround. Use 'shutdown --help' or read man shutdown to see all available options.

---

