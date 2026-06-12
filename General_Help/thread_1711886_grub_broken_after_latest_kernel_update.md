---
title: "grub broken after latest kernel update"
date: 2011-03-21
forum: General Help
---

### Post by skelloch on 2011-03-21
Ubuntu 10.10 latest kernel 2.6.35-28.49 update is broken.

update just stalls when it gets to this...
> Sub-process /usr/bin/dpkg returned an error code (1)...
generating grub.cfg

I have tried the following to no avail...

> sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgradeI have not changed any hardware. 

Thanks for your input/help.

---

### Post by Lianli on 2011-03-21
Ubuntu 10.10 running Trinity

I ran into trouble with kernel 2.6.35-28.49 freezing at boot, After tons  of fiddling it finally rebooted. Grub2.. Hmmm.. all i can say is (GRRRRR!) I  found it to be a total overkill for my needs and decided to switch to grub  legacy. My system seems to boots ok now despite a very long hang when  loading init scripts. 

Sorry I know this doesn't help you. just confirming i started having trouble after this kernel update as well.

---

### Post by skelloch on 2011-03-22
I used a ubuntu live cd to rescue system....
 > dpkg --configure -a

This fixed it. I still am curious as to why this worked but did not work the other way. I can't help it I am curious.

---

