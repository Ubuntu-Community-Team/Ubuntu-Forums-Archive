---
title: "auto-run script update-rc error"
date: 2010-09-21
forum: General Help
---

### Post by DragonDon on 2010-09-21
Hey All,

I found the directions to move the script to /etc/init.d/ directory but I am getting an error message when trying to update-rc

```
sudo update-rc.d /etc/init.d/myfirewall.sh defaults

update-rc.d: /etc/init.d//etc/init.d/myfirewall.sh: file does not exist
```

What's with the double slash that seemingly appears out of nowhere?

So I decided to run it from within the directory and that seemed to work...mostly:

```
sudo update-rc.d myfirewall.sh defaultsupdate-rc.d: warning: /etc/init.d/myfirewall.sh missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/myfirewall.sh ...
   /etc/rc0.d/K20myfirewall.sh -> ../init.d/myfirewall.sh
   /etc/rc1.d/K20myfirewall.sh -> ../init.d/myfirewall.sh
   /etc/rc6.d/K20myfirewall.sh -> ../init.d/myfirewall.sh
   /etc/rc2.d/S20myfirewall.sh -> ../init.d/myfirewall.sh
   /etc/rc3.d/S20myfirewall.sh -> ../init.d/myfirewall.sh
   /etc/rc4.d/S20myfirewall.sh -> ../init.d/myfirewall.sh
   /etc/rc5.d/S20myfirewall.sh -> ../init.d/myfirewall.sh
```

So, checking into LSB information only gets me confused.  Do I really need it?

---

