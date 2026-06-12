---
title: "Kernel panic - not syncing: Attempted to kill init"
date: 2011-09-22
forum: General Help
---

### Post by ivanp on 2011-09-22
Hello,

I've upgraded my Ubuntu 10.04 LTS installation and now it just won't boot. Kernel and user panic.

The installation is over a virtual machine. It uses GNU GRUB 1.97-beta4.
I've tried to boot from Ubuntu, Linux  2.6.31-23-generic and 2.6.31-14-generic. Both fail with the same error shown in recovery mode:

/sbin/init: error while loading shared libraries: /lib/libnih.so.1: file too short
[    3.747558] Kernel panic - not syncing: Attempted to kill init
[    3.749197] Pid: 1, comm: init not tainted 2.6.31-23-generic #75-Ubuntu
...

I've run the life CD and doesn't show any option for recovering and detects the installation as a Ubuntu 9.10...

I've backed up files now, but can't get the box running again.
What should I try now?

Thanks in advance

---

