---
title: "''sudo nautilus''command gives error in terminal"
date: 2010-11-09
forum: General Help
---

### Post by RastaManPower on 2010-11-09
this is what i am getting
***@***:~$ sudo nautilus
Initializing nautilus-gdu extension

** (nautilus:6425): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '6425'

(nautilus:6425): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by garvinrick4 on 2010-11-09
Alt/F2 and type in gksudo nautilus:

---

