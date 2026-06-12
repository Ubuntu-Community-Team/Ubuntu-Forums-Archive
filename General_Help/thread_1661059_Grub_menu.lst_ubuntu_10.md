---
title: "Grub menu.lst ubuntu 10"
date: 2011-01-06
forum: General Help
---

### Post by Dime-Sonia on 2011-01-06
Can't find this file!

---

### Post by ksprasad on 2011-01-06
You can't find it. Because, Ubuntu 10.10 uses Grub2, not Grub legacy.
 
Please go to this link.
 
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
 
Regards,
ksprasad

---

### Post by Dime-Sonia on 2011-01-06
> **ksprasad said:**
> You can't find it. Because, Ubuntu 10.10 uses Grub2, not Grub legacy.
 
Please go to this link.
 
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
 
Regards,
ksprasad

Can't change the boot priotity in grub.cfg!

---

### Post by Dime-Sonia on 2011-01-06
> **ksprasad said:**
> You can't find it. Because, Ubuntu 10.10 uses Grub2, not Grub legacy.
 
Please go to this link.
 
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
 
Regards,
ksprasad

Can't save it!

---

### Post by Verbeck on 2011-01-06
> **Dime-Sonia said:**
> Can't change the boot priotity in grub.cfg!
try changing it from the the file /etc/default/grub
```
gksu gedit /etc/default/grub
```change the value in **GRUB_DEFAULT=0** to the one you want to be the default 

0 = first entry
1 = second entry 
2 = third entry and so on...

**edit** : after that, you should run* sudo update-grub*

**edit again**:
> **Dime-Sonia said:**
> Can't save it!
you should open it with root privilages
```
gksu gedit */boot/grub/grub.cfg*
```

---

### Post by Dime-Sonia on 2011-01-06
> **Verbeck said:**
> try changing it from the the file /etc/default/grub
```
gksu gedit /etc/default/grub
```change the value in **GRUB_DEFAULT=0** to the one you want to be the default

0 = first entry
1 = second entry 
2 = third entry and so on...

Than't good

---

### Post by ksprasad on 2011-01-06
> **Dime-Sonia said:**
> Can't save it!
 
Even though you can make changes in grub.cfg, you should not try to do it. Because, it is auto-generated file. Your changes may be overwritten at any time.
 
Regards,
ksprasad

---

### Post by Krytarik on 2011-01-06
Nice guide here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

