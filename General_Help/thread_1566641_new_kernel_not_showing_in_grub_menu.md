---
title: "new kernel not showing in grub menu"
date: 2010-09-02
forum: General Help
---

### Post by Dilutu on 2010-09-02
Hi all.
Every time I update my kernel (today with 2.6.32-25-generic), I always have to manually run "sudo update-grub" or ells the new kernel does not show up on reboot??? Is there a config some place to get it back to automatic??
Th.

---

### Post by Dilutu on 2010-09-03
B....u....m....p....!!!!!!

---

### Post by Dilutu on 2010-09-11
bump...bump

---

### Post by Dilutu on 2010-11-09
Well again today updated to 2.6.32-26 generic and still no new kernel in my grub list on reboot??

---

### Post by dcstar on 2010-11-09
> **Dilutu said:**
> Well again today updated to 2.6.32-26 generic and still no new kernel in my grub list on reboot??

Check /etc/kernel-img.conf:

```
do_symlinks = yes
relative_links = yes
do_bootloader = no
do_bootfloppy = no
do_initrd = yes
link_in_boot = no
[B]postinst_hook = update-grub
postrm_hook = update-grub[/B]
```

---

### Post by Dilutu on 2010-11-09
Wow thanx for the fast answer! I checked this file and the last 2 lines were missing. 
Have a nice day. Th.

---

### Post by ralic on 2011-06-26
Convinced my grub was borked, I've spent a fruitless day uninstalling and re-installing grub in every way, shape and form possible, without success.

Thanks for this! It worked like a charm.

keywords: update-grub not triggered after kernel update

---

