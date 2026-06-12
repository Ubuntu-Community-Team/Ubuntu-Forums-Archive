---
title: "uninstall ubuntu"
date: 2012-04-26
forum: General Help
---

### Post by neophyte02 on 2012-04-26
Hi,

I have windows 7 and ubuntu 10.04 on my system.i now want to remove ubuntu 10.04 and install 12.04 on my system?
what is the safest procedure to do this so that my system is not affected in any way??

---

### Post by kc1di on 2012-04-26
> **neophyte02 said:**
> Hi,

I have windows 7 and ubuntu 10.04 on my system.i now want to remove ubuntu 10.04 and install 12.04 on my system?
what is the safest procedure to do this so that my system is not affected in any way??
you can install ubuntu 12.04 right over 10.04 insert the cd or usb boot to live ubuntu and click on install when the partitioning page come up click on other.  (I'm assuming 10.04 was not a WUBI install) find the current ubuntu partition (EXT3 or 4) click on change select ext 4 then mountpoint / it will format the and erase the old 10.04 install and install new 12.04.  **IMPORTANT NOTE: It is always good to back up any important data before doing a new install just in case!**

Good Luck,
D :)

---

### Post by neophyte02 on 2012-04-26
> **kc1di said:**
> you can install ubuntu 12.04 right over 10.04 insert the cd or usb boot to live ubuntu and click on install when the partitioning page come up click on other.  (I'm assuming 10.04 was not a WUBI install) find the current ubuntu partition (EXT3 or 4) click on change select ext 4 then mountpoint / it will format the and erase the old 10.04 install and install new 12.04.  **IMPORTANT NOTE: It is always good to back up any important data before doing a new install just in case!**

Good Luck,
D :)

do i need to format swap drive and boot drive? i want to completely remove all the records of present ubuntu and install a new one. so, which is the good way to do that?

---

### Post by IWantFroyo on 2012-04-26
It should be as simple as selecting "Replace Ubuntu 10.04" on installation.

If the option is there, try it.

Back up, always.

And also, you don't need to format anything. The system should do that for you.

---

### Post by neophyte02 on 2012-04-26
thanx guys for the reply

---

### Post by kc1di on 2012-04-27
> **neophyte02 said:**
> thanx guys for the reply

Your Welcome how did you make out?

---

### Post by neophyte02 on 2012-04-27
haven't done it yet. i've one more query: when i replace old ubuntu will it replace old grub also or what?

---

### Post by techsupport on 2012-04-27
> **neophyte02 said:**
> haven't done it yet. i've one more query: when i replace old ubuntu will it replace old grub also or what?

Yeah it sure will. No worries. :) 

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

---

