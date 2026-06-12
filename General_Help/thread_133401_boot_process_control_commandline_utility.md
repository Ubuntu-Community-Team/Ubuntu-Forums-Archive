---
title: "boot process control commandline utility"
date: 2006-02-20
forum: General Help
---

### Post by soongwoo on 2006-02-20
Is there any commandline utility to control boot processes along with runlevel?
I have to write a script which automates the system customization,
such as installing apache2 package, not starting vsftpd at boot, etc.

I know there are utilities such as bum, sysv-rc-conf with gui.
But, I can not use them.

Thanks
soongwoo

---

### Post by schilcha on 2006-02-20
maybe "update-rc.d" helps...

---

### Post by soongwoo on 2006-02-21
Thanks schilcha.
I'll try the command for wrting customization script.

soongwoo

---

