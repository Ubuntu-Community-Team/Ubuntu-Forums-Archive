---
title: "sudo nautilus error messages"
date: 2011-01-21
forum: General Help
---

### Post by RussellEngland on 2011-01-21
I use "sudo nautilus" from a terminal window when I need to access files and folders as root. But the terminal keeps showing these messages. It doesn't seem to affect Nautilus at all though. 

```

russ@russ-laptop:/home$ sudo nautilus

Initializing nautilus-dropbox 0.6.6
Initializing nautilus-gdu extension

** (nautilus:9224): WARNING **: Failed to get the current CK session:  GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to  lookup session information for process '9224'

(nautilus:9224): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net  usershare' returned error 255: net usershare: cannot open usershare  directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```

---

### Post by tredegar on 2011-01-21
Try **gksu nautilus**

---

### Post by 3Miro on 2011-01-21
You should never use "sudo nautilus". The correct command is:

```
gksudo nautilus
```

---

### Post by RussellEngland on 2011-01-21
Brill!! 

gksudo nautilus doesn't give error messages

Thank you :)

I'm still fairly new - I'm presuming that gksudo is for graphical applications and sudo for command line?

---

### Post by tredegar on 2011-01-21
> I'm presuming that gksudo is for graphical applications and sudo for command line?
Yes. You got it right.

---

