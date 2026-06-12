---
title: "Cannot install Gparted"
date: 2009-07-17
forum: General Help
---

### Post by os56k on 2009-07-17
I wanted to install Gparted through the Add/Remove in Applications menu but it gave my the following error :

"Another Synaptic is Running"

---

### Post by devosion on 2009-07-17
Make sure you aren't using aptitude through terminal, or have the package manager window open. Even an occuring update while trying to install new software will cause ubuntu to throw this message at you.

---

### Post by os56k on 2009-07-17
Thank you very much devasion. a program installation was running. I closed it and then I could download and install Gparted. Now I have it on System->Administration.

---

### Post by CatKiller on 2009-07-17
Don't forget that you can't change a partition that's mounted, and running GParted from an install means that / is necessarily mounted, so you can't change that partition. If you need to change any of your Linux partitions, it's usually best to do so from a live cd like the Ubuntu install disc or GParted's own [live cd]("http://gparted.sourceforge.net/livecd.php").

---

### Post by os56k on 2009-07-23
Thank you all for your guide. With your help be certain that Microsoft will not be the only authority for operating system.:o

---

