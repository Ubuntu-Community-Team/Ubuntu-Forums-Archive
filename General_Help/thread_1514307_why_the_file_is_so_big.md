---
title: "why the file is so big?"
date: 2010-06-20
forum: General Help
---

### Post by luofeiyu on 2010-06-20
in  my  sda7 ,there is nothing in it ,just an empty file :lost+found
it has 927M  ,why?
please see my  attachment

---

### Post by juancarlospaco on 2010-06-20
i dont see the details because of the screenshot app window in top,
but these folder can contain, root related things, 
generated when you use sudo on any program,
to try to clean up, you can run bleachbit as root, 
and perform a disk check, with : 
sudo touch /forcefsck && sudo reboot

---

