---
title: "Kernel panic after &quot;exit&quot; from BusyBox"
date: 2011-11-19
forum: General Help
---

### Post by antoiner_roquentin on 2011-11-19
When I boot my netbook (which was working fine for weeks with 11.04) it loads the generic GNU GRUB. When I try to boot Ubuntu it goes to the normal BusyBox with "(initramfs)" on the command line.

I type exit to try to get the system to boot and it returns this:

[539.644987] Kernel panic - not syncing: Attempted to kill init!
"                  " Pid: 1, comm: init Tainted: G        D         2.6.38-8-generic #42-Ubuntu

Followed by a bunch of stuff about "call trace".

I am at a loss for what to do here.

---

### Post by antoiner_roquentin on 2011-11-19
Still no luck with this problem, does anyone have some insight?

---

### Post by LinuxFan999 on 2011-11-19
Your installation is broken. You need to reinstall Ubuntu.

---

