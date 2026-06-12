---
title: "mount windows partition"
date: 2010-04-05
forum: General Help
---

### Post by panti19 on 2010-04-05
installed xubuntu using wubi (i had 2 partitions , one with the windows installations and all my files and another one which was empty for xubuntu)
it has successfully installed the system but i can't find my windows files.
help

---

### Post by mickObrian on 2010-04-05
Are your Windows partitions NTFS formatted? Try installing NTFS-3g, it's default installed in Ubuntu, not sure about Xubuntu, being a lighter system it may not.

---

### Post by hhh on 2010-04-05
From the Wubi FAQ...

> Can I access my Windows files from a Wubi installation?

Yes, the Windows partitions will be available within the directories /host and /media.

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by Morbius1 on 2010-04-05
I don't use wubi but if I remember correctly you can find them in either /host or /media on your ubuntu system.

[COLOR=Blue]OOPS, sorry about that - simultaneous posts it seems. [/COLOR]

---

### Post by panti19 on 2010-04-05
thanks but in host, only the partition holding the installation is shown. not the other one containing the windows installation

---

### Post by panti19 on 2010-04-05
solved it.
used ntfs configuration tool

---

### Post by garvinrick4 on 2010-04-05
I really do not think in a WUBI install if you can see other partition other than the host.
It is not mounted so you cannot use samba. I have one WUBI install left on a Vista machine
and it is not visable in my workgroup yet 5 other 3 linux and 2 windows are visable. In laptop
all 3 are visable 7, karmic, and lucid.  If you find anything please post on your thread.

---

### Post by garvinrick4 on 2010-04-05
> **panti19 said:**
> solved it.
used ntfs configuration tool
Where does the other windows partition show up in WUBI install? The one wubi
is installed in is has a host directory and where does the other partition show up?

---

### Post by panti19 on 2010-04-06
the other partition i believe was in media
i can't check now, as i uninstalled xubuntu. did my job with it. will do a clean install.

---

