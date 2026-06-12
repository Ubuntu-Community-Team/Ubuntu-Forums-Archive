---
title: "Unable to log in"
date: 2009-10-04
forum: General Help
---

### Post by Gazzman on 2009-10-04
I have just installed Ubuntu 9.04 inside Windows XP.
The install seemed fine. But now when I boot into ubuntu I notice an -110 error and it won't let me log in.

I'm new to ubuntu. Can anyone offer suggestions.

Thanks

---

### Post by ermeyers on 2009-10-04
Not sure what you mean by "inside Windows XP."  Ubuntu is typically installed from a CD boot of the Ubuntu CD.

---

### Post by sendblink23 on 2009-10-04
> **ermeyers said:**
> Not sure what you mean by "inside Windows XP."  Ubuntu is typically installed from a CD boot of the Ubuntu CD.

he means WUBI  install which is ubuntu installed within windows

Anyways to help you out...  I Would Erase that Wubi you first made & try it again.. something probably went wrong on your first install

---

### Post by ermeyers on 2009-10-04
>  ubuntu installed within windows
I'd rather shooting myself in the foot.

---

### Post by Gazzman on 2009-10-05
I installed a dual boot.
Grub loads 
I'm able to get into XP but can't log into Ubuntu 9.04
I hope I have the right terminology. Like I said I'm new to Ubuntu

---

### Post by louieb on 2009-10-05
> **Gazzman said:**
> I installed a dual boot.
Grub loads 
I'm able to get into XP but can't log into Ubuntu 9.04
I hope I have the right terminology. Like I said I'm new to Ubuntu

WUBI creates a virtual file-system for Ubuntu inside your windows partition. If you go to windows add-remove programs and see Ubuntu as one of the options then a WUBI install is what you have. 

Another way to tell - Ubuntu or windows listed first in the "GRUB" menu? If its windows the you are looking at the windows boot loader. - not GRUB.

WUBI is the easiest way to install Ubuntu on a hard drive. When it works its ok. But when things go wrong its the hardest to fix. Everything I know about fixing a WUBI Ubuntu install can be found here. [WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide")

> **ermeyers said:**
> I'd rather shooting myself in the foot.

Nice description of a WUBI install. :P

---

### Post by Gazzman on 2009-10-09
Thanks to all who tried to help.

I lowered my resolution and removed the @ character from my password and the dual boot works

---

