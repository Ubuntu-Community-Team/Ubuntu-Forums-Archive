---
title: "How to remove vt.handoff=7 parameter???"
date: 2011-05-27
forum: General Help
---

### Post by dancer_69 on 2011-05-27
I have always boot hang with black screen and flashing cersor when trying to reboot Ubuntu 11.04.
And I finally found that the problem is this new vt.handoff=7 option.
So I tried to remove this option by editing the /etc/default/grub, but I found that this option doesn't exist in this file.
It's still there in every reboot though.
So where is???

---

### Post by mc4man on 2011-05-27
try removing quiet and splash, that should also remove the vt.handoff=7

---

### Post by dancer_69 on 2011-05-27
I solve it myself.
After a research on all grub related config files(/boot/grub/grub.conf, /etc/grub.d files, /etc/default/grub) and some testing & reboots I found that in 10_linux file there is the following line:
GRUB_CMDLINE_LINUX="rootflags=subvol=${rootsubvol} ${GRUB_CMDLINE_LINUX} vt.handoff=7"

which automatic regenerate this option, even if removed from /etc/default/grub file.
Remove it and update-grub fixed it.

---

### Post by Sparohok on 2011-06-05
In 11.04 it seems to be fixed, "vt.handoff=7" is only added if "splash" is in GRUB_CMDLINE_LINUX_DEFAULT.

---

### Post by TREESofRIGHTEOUSNESS on 2013-02-19
> **dancer_69 said:**
> I solve it myself.
After a research on all grub related config files(/boot/grub/grub.conf, /etc/grub.d files, /etc/default/grub) and some testing & reboots I found that in 10_linux file there is the following line:
GRUB_CMDLINE_LINUX="rootflags=subvol=${rootsubvol} ${GRUB_CMDLINE_LINUX} vt.handoff=7"

which automatic regenerate this option, even if removed from /etc/default/grub file.
Remove it and update-grub fixed it.

Could you please mark this thread as solved?

Also for newer users you can find the 10_linux file in
/etc/grub.d

---

### Post by oldos2er on 2013-02-19
Old thread closed.

---

