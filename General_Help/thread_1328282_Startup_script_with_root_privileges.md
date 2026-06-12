---
title: "Startup script with root privileges"
date: 2009-11-16
forum: General Help
---

### Post by tomcat2007 on 2009-11-16
Is there something that runs at startup with root privileges to which I can attach a script of my own?  I want to set my CPU scaling to conservative automatically without having to type a password every time my laptop powers up.  Have already tried attaching to /etc/rc.local, to no avail.

Thanks.

---

### Post by philinux on 2009-11-16
```
gksu gedit /etc/init.d/ondemand
```

Change the default ondemand to conservative. Line 27. Helps if you turn on line numbering in gedit.

Needs a reboot to take effect.

---

### Post by tomcat2007 on 2009-11-16
> **philinux said:**
> ```
gksu gedit /etc/init.d/ondemand
```

Change the default ondemand to conservative. Line 27. Helps if you turn on line numbering in gedit.

Needs a reboot to take effect.
Thanks for the suggestion... tried it & waited well past the 60 second sleep period specified in the script but the CPUs did not scale down.  They actually default to performance mode which makes me wonder if the system is even looking in that file.  Is there a Linux world version of the old DOS autoexec.bat?

Am using Karmic 64 bit.

---

