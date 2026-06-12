---
title: "Default user's usergruops"
date: 2011-01-14
forum: General Help
---

### Post by ZebaSz on 2011-01-14
After the events mentioned in [this thread]("http://www.ubuntuforums.org/showthread.php?t=1662168"), I had to create a new user from the recovery console, and delete my previous one. Problem is, I noticed the new user was not added to any group. I did add it to "admin", in order to be able to manage my system properly, but I don't know which other gruops I should add it to.
The user I'm talking about currently is (and will continue to be) the only user in the system besides root, so I'd need to add it to the exact same groups the default installation user is in.

---

### Post by sisco311 on 2011-01-14
If you add a new admin user to the system via the GUI (admin-users from gnome-system-tools), the user is added to the following groups:

**cdrom,floppy,dialout,tape,dip,adm,plugdev,fax,fuse,admin,sambashare,lpadmin,video**

```
sudo usermod -aG cdrom,floppy,dialout,tape,dip,adm,plugdev,fax,fuse,admin,sambashare,lpadmin,video **username**
```

---

### Post by ZebaSz on 2011-01-15
Great, thanks. Hadn't thought of that method, could have done it myself.

---

