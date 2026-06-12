---
title: "Accesing files belonging to root even if... you are root"
date: 2011-04-18
forum: General Help
---

### Post by PCaddicted on 2011-04-18
Hi,
I have Ubuntu 10.10 and I can't open the rkhunter logfile(I did a scan with rkhunter some time ago).I can't open it,nor make it executable because "I am not the owner".The owner appears to be root at Properties>Permissions.I opened the terminal,logged as root and typed the path to the log file.I got Permission Denied.Is there a glitch somewhere or is Ubuntu as unobedient as Windows?

---

### Post by deathadder on 2011-04-18
> **PCaddicted said:**
> Hi,
I have Ubuntu 10.10 and I can't open the rkhunter logfile(I did a scan with rkhunter some time ago).I can't open it,nor make it executable because "I am not the owner".The owner appears to be root at Properties>Permissions.I opened the terminal,logged as root and typed the path to the log file.I got Permission Denied.Is there a glitch somewhere or is Ubuntu as unobedient as Windows?
What are the full permissions on the file? For the owner, group and everybody. If you can't see these in a file browser (right click on the file and choose properties) then post the output of:
```
ls -lh /path/to/file
```
It could be that the app used to create the file ran under a different user, or remove read/write permission for some user / groups.

---

### Post by PCaddicted on 2011-04-18
I am the only user.
Permissions output for that file:
-rw------- 1 root root 122K 2011-04-16 14:44 /var/log/rkhunter.log.1
Note that I have another log file from an earlier rkhunter scan(rkhunter.log),and I can access that one...weird.

---

### Post by deathadder on 2011-04-18
Ok, so that tells us the root user has read and write permission on the file. The group "root" has no permissions to view, or modify the file. The same applies for everyone else. 

You can run "gksu nautilus", by pressing Alt-F2, to start nautilus as the root user, you will then be able to view and if you want modify the permission. Not that I would suggest doing that. 

If you need to change the file, I would suggest copying it to a different location, and then right clicking on it and choosing "Properties" to modify permissions.

Not sure why the other log files for rkhunter have different permissions though...

---

### Post by PCaddicted on 2011-04-20
I ran Nautilus as root and I could access the file.Thanks for help.

---

### Post by deathadder on 2011-04-21
I'm sure I don't need to say this but "be careful when you run apps as root!" It's generally a better idea to use sudo as and when you can. Glad it worked for you though.

---

