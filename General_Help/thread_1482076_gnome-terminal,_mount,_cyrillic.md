---
title: "gnome-terminal, mount, cyrillic"
date: 2010-05-13
forum: General Help
---

### Post by RRJ on 2010-05-13
Hello,

i've got such problem:
im running ubuntu 10.04 on notebook and winxp on deskpc.
all i need is to get cyrillic working with gnome-terminal

i mount my samba-share with
mount //server/folder /mnt/win -u username=username,dir_mode=0777,file_mode=0777
mounting works fine
then i do 
ls -l /mnt/win
and instead of cyrillic letters all i see is ?????? ??? ?? ??  and terminal says - there is no such file blablabla.
i've tried to change the encoding in topmenu -> terminal -> encoding and ctrl+l - nothing.

any ideas? i think there must be something with mount...
at the same time i can write with cyrillic in terminal and nautilus sees those russian letters fine. the problem is only with gnome-terminal seems...

---

### Post by RRJ on 2010-05-13
bump.. hate it, but bump. need a salvation.

---

### Post by RRJ on 2010-05-13
any ideas?

---

### Post by RRJ on 2010-05-14
common, any question i ever asked here never answered. kind of a nice community.

---

### Post by RRJ on 2010-05-14
well, like always.
got it by myself. had to add iocharset=utf8

do you guys ever help people? :)

---

