---
title: "Reload built-in kernel driver?"
date: 2009-09-19
forum: General Help
---

### Post by Cenoforums on 2009-09-19
Hi,

Given a normal kernel module, one can reload it by running rmmod and then a modprobe.
How can we do this if the module is now built-in to the kernel?

Module in question is uhci_hcd. Used to solve a detection problem I had with a usb modem by removing and reloading the module. I had a script for that, which now naturally doesn't work...

---

### Post by Cenoforums on 2009-09-20
In the discussion going on in this [link]("http://forum.soft32.com/linux2/SATA-driver-built-loadable-module-ftopict16973.html") someone said that

| Ehh ... I don't usually compile modules I don't plan to use. But if 
| everything is built-in, the only way to "fix" a subsystem in a serious 
| state of confusion is a reboot. The USB host controller halt I was 
| writing about used to happen a couple of times each day (on most 
| days). A quick rmmod -f/ modprobe was faster than rebooting the box 
| would have been.

So it seems that it is impossible to manually reload a builtin module.

Can someone please confirm this?

---

### Post by Whiffle on 2009-09-20
I don't think you can.

---

