---
title: "transfer Firefox profile from Ubuntu to Ubuntu"
date: 2010-06-23
forum: General Help
---

### Post by surrealillusions on 2010-06-23
Hi all,

Is there an easy way to transfer the Firefox profile from one computer to another? Both running Ubuntu 10.04, and FF 3.6.

Is it just a case of transfering the folders over via usb stick?

---

### Post by lifeSum on 2010-06-23
The profiles are stored in:
```
/home/username/.mozilla/firefox/
```If you copy that folder over to the same location on the other computer, it should work.

---

### Post by surrealillusions on 2010-06-23
Cool, worked like a charm.

Thanks :)

---

### Post by lovinglinux on 2010-06-23
You can also use FEBE extension, which I recommend for regular backups.

See the [Backup](http://firefox-tutorials.blogspot.com/2010/05/backups.html) section of  [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

