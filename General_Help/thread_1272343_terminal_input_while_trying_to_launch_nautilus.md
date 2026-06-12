---
title: "terminal input while trying to launch nautilus"
date: 2009-09-22
forum: General Help
---

### Post by dogafin on 2009-09-22
> **dogafin said:**
> dogafin@dogafin-desktop:~$ sudo nautilus
Fontconfig error: "~/.fonts.conf", line 2: no element found
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:4383): WARNING **: Unable to add monitor: Operation not supported

nautilus starts but i get this message and its starting to annoy me like something is wrong that needs fixing. someone help?

---

### Post by P4man on 2009-09-22
you should always use **gksudo** instead of sudo to launch a graphical program (like nautilus). Not that that will solve your issue, because afaict, you have no issue :). Those are warnings, don't worry about them, most apps tend to be quite verbose when you launch them from a terminal. It looks like nautilus is trying to find network shares and fails because you don't have any.

---

### Post by dogafin on 2009-09-25
fixed my own problem. launched nautilus and went to /var/lib/samba
and created an empty file named usershares

---

