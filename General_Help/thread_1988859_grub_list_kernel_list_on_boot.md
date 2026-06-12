---
title: "grub list kernel list on boot"
date: 2012-05-28
forum: General Help
---

### Post by teriyaki-89 on 2012-05-28
Hi i am trying to find how to make grub list kernel menu and not boot default but can't find it.  I used /etc/default/grub  and updated grub2  but still no luck
Can anyone help me on ubuntu 12.04?


#GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


in example i see this but no parameter to list kernels on boot, Esq does not help on boot
info -f grub -n 'Simple configuration'

---

### Post by plucky on 2012-05-28
> **teriyaki-89 said:**
> Hi i am trying to find how to make grub list kernel menu and not boot default but can't find it.  I used /etc/default/grub  and updated grub2  but still no luck
Can anyone help me on ubuntu 12.04?


#GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


in example i see this but no parameter to list kernels on boot, Esq does not help on boot
info -f grub -n 'Simple configuration'

Look [Here](http://ubuntuforums.org/showthread.php?p=10340183#post10340183) and install Grub Customizer from the PPA and you can select to display the boot menu and other things.

Good Luck

---

