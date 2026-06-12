---
title: "grub configuration reset"
date: 2010-06-02
forum: General Help
---

### Post by wirate on 2010-06-02
Whenever there is a kernel upgrade, "update-grub" is run and my customized "/boot/grub/grub.cfg" is gone. is there any way to prevent this?
Thank you

---

### Post by gzarkadas on 2010-06-14
grub.cfg is not meant to be directly editable; it is recreated whenever update-grub is run. You 'll have to put your customisations inside the scripts in /etc/grub.d/ directory (and maybe modify /etc/default/grub also). See for details [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2), especially sections 7 and 10.

---

