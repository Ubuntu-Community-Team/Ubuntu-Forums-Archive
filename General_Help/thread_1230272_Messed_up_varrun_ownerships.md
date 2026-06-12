---
title: "Messed up /var/run ownerships"
date: 2009-08-03
forum: General Help
---

### Post by wdpreez1 on 2009-08-03
I messed up the owners (and groups) of the directories, sub-directories and files in /var/run of my 9.04 server installation by doing ```
sudo chown -R openldap.openldap *
```in /var/run so a few things don't work because they can't write to /var/run/<foo>

I have figured out who the owner.group of some dirs should be, and manually fixed them. However, something restores it to the messed up state on reboot.

So: (1) what restores the wrong owners and how do I stop it from re-messing things up?, and (2) where can I get the correct owners for /var/run (an 'ls -lR /var/run' from a healthy 9.04 server system will do quite nicely)

Thanks in advance

Wessel

---

