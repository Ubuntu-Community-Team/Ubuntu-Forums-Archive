---
title: "how to share subversion repository between windows and ubuntu?"
date: 2010-01-28
forum: General Help
---

### Post by creatxr on 2010-01-28
how to share subversion repository between windows and ubuntu?

i've subvserion repository on NTFS.
i wish i can use it on ubuntu.
but :
"Can't open directory '/media/WIN_DATA/SVN_HOME': Permission denied"
i try "chmod 777 -R /media/WIN_DATA/SVN_HOME".
it's also unuseful.
possible? how to?

---

### Post by rnerwein on 2010-01-28
hi
the chmod don't work for you. i think you have to modify your /etc/fstab. here is my entry and it works.
/dev/sda3 /vista_data ntfs defaults,noauto,umask=000
(sda3 and vista_data you must change to your behavior. even when you want to automount your partition you have to change "noauto" to "auto".
ciao

---

