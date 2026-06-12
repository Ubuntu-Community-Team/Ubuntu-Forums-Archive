---
title: "after re-installing windows xp ,grub2 menu does not showup"
date: 2010-09-02
forum: General Help
---

### Post by abs_kkk on 2010-09-02
firstly i am completely new to linux so i don't know much about it,yesterday i installed win xp on my pc which already has ubuntu 9.10 karmic koala installed on a seperate partition,after xp was installed and when it rebooted ,a dos screen showed up with sh:grub> command ,how do i get to the grub menu where i can boot into xp or ubuntu?

---

### Post by anirudhtomer on 2010-09-02
Boot with your live CD & click on try ubuntu without change.
then open the terminal & type the following.

$ grub
this will start the program grub

grub> find /boot/grub/stage1

then u'll get something like (hd0,4)
u may get any other value ....

grub> root(hd0,4)
grub> setup(hd0)

I hope your problem gets solved.

look at this link as well [http://ubuntuforums.org/showthread.php?t=1558550](http://ubuntuforums.org/showthread.php?t=1558550)

---

### Post by abs_kkk on 2010-09-02
after i typed the command(grub> find /boot/grub/stage1) in grub
i got

Error 15: File not found

not sure wats the file.....

---

### Post by abs_kkk on 2010-09-02
i googled that erro it looks some how related to the old grub legacy one , but i have grub 2 ,is it related to both grub legacy and grub2?

---

