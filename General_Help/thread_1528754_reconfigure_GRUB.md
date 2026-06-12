---
title: "reconfigure GRUB"
date: 2010-07-11
forum: General Help
---

### Post by veehexx on 2010-07-11
having read through [https://help.ubuntu.com/community/GrubHowto#head-44a5805eeda20ec1b6bd6c274cbf3a74230675d1](https://help.ubuntu.com/community/GrubHowto#head-44a5805eeda20ec1b6bd6c274cbf3a74230675d1) for info, it seems my question isnt covered...

basically, i was running windows7. i grabbed an ISO i had (10.04 desktop x86), and used the wubi installer to install ubuntu. this obtained 10.04 alt x64 and installed it.

everything went smoothly so i proceeded with updating it with the latest security fixes&updates. i seem to recall a GRUB update being done, but was unable to click 'ok', 'next' or something like that, so i had to click CANCEL. GRUB didnt get updated/configured fully.

upto here, everything is working the way it should, but not the way i want.

however, i have 2 boot menus now. the first is the windows one; with 'windows7' and 'ubuntu' listed.
if i select ubuntu, it then loads the GRUB boot menu.

is it possible to remove the windows boot menu and replace it with GRUB, so i only have 1 boot menu?

i have reconfigured windows to 3 seconds display time, and ubuntu as the default option so it's not a huge problem, but would be nice to have just 1 boot menu

---

### Post by Mark Phelps on 2010-07-11
> **veehexx said:**
> ... is it possible to remove the windows boot menu and replace it with GRUB, so i only have 1 boot menu?

Basically -- NO.  

Had you NOT installed using Wubi, there would be ways to use GRUB to boot into either MS Windows or Ubuntu, but with Wubi, you have to use the MS Windows boot loader because Wubi performs the install from "inside Windows" (although Ubuntu, once launched, does not actually RUN inside Windows).

---

### Post by veehexx on 2010-07-11
shame. i'll have a play with boot menu countdowns then. i THINK win7 is listed under the grub menu, so i should be able to set the windows boot menu to 0 countdown essentially removing it from view.

---

### Post by markjreed on 2010-08-25
> **veehexx said:**
> shame. i'll have a play with boot menu countdowns then. i THINK win7 is listed under the grub menu, so i should be able to set the windows boot menu to 0 countdown essentially removing it from view.

Have you tried actually booting from the Windows option on the grub menu?  Doesn't work for me.  The only way I can get to Windows is from the Windows bootloader.

---

