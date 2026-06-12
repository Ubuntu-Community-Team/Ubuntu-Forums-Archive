---
title: "Virtual Network Device - Unable to start services."
date: 2010-06-15
forum: General Help
---

### Post by surrealillusions on 2010-06-15
Hi,

Just upgraded fro 9.10 to 10.04, and went to start VMware player. It needed to load and compile some modules.

All of them got a nice green tick except the Virtual Network Device

Unable to start services.
See log file /tmp/vmware-root/setup-2986.log for details.

I cant access that log file. Set the folder to read only, and any contents, but theres no file in there.

How do I solve this so I can run WMware??

Thanks
:)

---

### Post by maedox on 2010-06-15
The first thing to do is get some output so we know what's causing the issues.
Do this:
```
sudo chmod -R 777 /tmp
```
And see it the log files shows up (after doing the start process again of course).

---

### Post by surrealillusions on 2010-06-15
By installing the newest version from vmware's site, it seems to work all fine now.

:)

---

### Post by maedox on 2010-06-16
Great. :D
Mark this thread as solved.

---

