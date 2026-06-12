---
title: "Update 10.04LTS configure grub-pc??"
date: 2011-06-19
forum: General Help
---

### Post by ScottEChapman on 2011-06-19
So, just did an update to my Ubuntu 10.04LTS system (single boot, nothing fancy) and I am presented with an option to configure grub-pc.

Not sure what the hell I should do at this point, should I NOT install it? Or should I proceed?

---

### Post by dino99 on 2011-06-19
for sure you need it :)

when it ask for config, have you seen/checked the help button to let you know about choices and differences ?

 Grub-pc (grub2) replace grub-legacy (grub1) & menu.lst, so remove/purge them before installing grub-pc & grub-common

If you dont want/need a custom grub menu (except of special hardware issue), simply accept the "default maintainer" choice

---

### Post by ScottEChapman on 2011-06-19
Per a previous post, I was able to reboot, and run dpkg --configure -a and I get this

> â You chose not to install GRUB to any devices.  If you continue, the boot  â
 â loader may not be properly configured, and when your computer next        â
 â starts up it will use whatever was previously in the boot sector.  If     â
 â there is an earlier version of GRUB 2 in the boot sector, it may be       â
 â unable to load modules or handle the current configuration file.          â
 â                                                                           â
 â If you are already running a different boot loader and want to carry on   â
 â doing so, or if this is a special environment where you do not need a     â
 â boot loader, then you should continue anyway.  Otherwise, you should      â
 â install GRUB somewhere.                                                   â
 â                                                                           â
 â Continue without installing GRUB?            

My update is "finished" except for this dpkg step.

---

### Post by dino99 on 2011-06-19
use synaptic to install grub-pc, that it.

or

sudo apt-get install grub-pc
sudo dpkg-reconfigure grub-pc

---

### Post by ScottEChapman on 2011-06-19
Tried to manually fix per suggestion.

> root@zimbra:~# apt-get install grub-pc
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
root@zimbra:~# dpkg-reconfigure grub-pc
/usr/sbin/dpkg-reconfigure: grub-pc is broken or not fully installed

When I run dpkg --configue -a I get that configure grub-pc dialog.

I am not saying I don't want to configure it, I just am not sure exactly what it is and if I SHOULD configure it, and how I would configure it. Like I said, my machine is 10.04LTS and is NOT a dual-but or anything like that. It was a clean install of 10.04LTS about 6 or so months ago...

---

