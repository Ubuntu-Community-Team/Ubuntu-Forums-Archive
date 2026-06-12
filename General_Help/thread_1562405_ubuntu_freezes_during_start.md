---
title: "ubuntu freezes during start"
date: 2010-08-27
forum: General Help
---

### Post by petex on 2010-08-27
It will neither start in normal nor in safe mode. the system loads but there's no splash screen. 
(actually i did not have a splash screen even before just after installing grub2 it stoped appearing and there was only some irregular artifacts on the screen but the system loaded at thah time)

now it will just freeze after laoding with no graphics on and just some before mentioned graphical trash in the meantime - I can turn off the system with powwrr button but i cannot do anything else e.g. ALT + CTR +f1 does no good 

what should i check or what can i do to recover the system (I'd rather avoid reinstalling it)

---

### Post by samn122 on 2010-08-27
Can you boot from a live CD?

---

### Post by Rubi1200 on 2010-08-27
How much RAM is installed and what graphics card do you have?

---

### Post by petex on 2010-08-28
yes i can start from liveCD
i have asus n80vn-gpc011 i.e. 4GB ddr2 RAM, nvidia m9650GT
there used to be some issues with GPU bfore but after upgrading firmware it all worked smoothly 
might be that i somtimes use dual screens but it did not happend after switching as far as i remember

---

### Post by petex on 2010-09-03
any advice?

---

### Post by Rubi1200 on 2010-09-03
There are a couple of things you can look at:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
This may help with issues at boot time.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765)
This bug report may help with possible workarounds other people have tried.

---

