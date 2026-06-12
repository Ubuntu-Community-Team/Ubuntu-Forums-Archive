---
title: "Update waxed grub"
date: 2010-02-06
forum: General Help
---

### Post by pcjunkie on 2010-02-06
A recent update for Karmic waxed my duel boot. Menu list no longer displays, #sudo update-grub does nothing. Worked fine since Karmic install then yesterday, hosed...

---

### Post by warfacegod on 2010-02-06
If you have an install disc, use it to reinstall GRUB.

---

### Post by warfacegod on 2010-02-06
This may be useful:

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2")

---

### Post by pcjunkie on 2010-02-06
Grub (v1) seems so much easier than grub 2

Thanks for the help. Nutting through this list slowly....
Seems the update changed etc/default/ grub.cfg file from

> GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


to

> GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


So the boot list did not display...
Simple error = so much farting around..:p

---

