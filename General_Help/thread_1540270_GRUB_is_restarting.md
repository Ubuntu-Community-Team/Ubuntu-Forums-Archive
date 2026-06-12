---
title: "GRUB is restarting"
date: 2010-07-27
forum: General Help
---

### Post by alikara on 2010-07-27
Hi 

I have a Samsung N150 netbook. Karmic and WinXP PRO run on it.

Karmic is opening healthy, if it was shutdown from Karmic. If it was shutdown from Windows: 
GRUB menu is opening,
I choose Karmic,
machine is restarting,
then GRUB menu is opening,
I choose Karmic, then it is restarting,
then GRUB is opening and Karmic is opening healty.

Kernel : 2.6.31-22-generic

I suppose it is because of GRUB. What do you think about it?
I googled it, but couldn't find anything.

P.S: If I shutdown Ubuntu and try to open Windows, it is restarting once.

Thanks in advance.

Ali

---

### Post by quixote on 2010-07-30
Given that it happens after a shutdown from Windows, my guess is that Windows is setting some sort of flags that it shouldn't be.  I don't think it's anything to do with grub.  It may take a few boot attempts to clear the flags. :?:

It's annoying and disquieting though.  I wish I knew a solution!

---

### Post by jsyl on 2010-07-30
A simple command within Karmic like
```
sudo update-grub
```
could fix the problem. I'm not 100% sure though.

---

