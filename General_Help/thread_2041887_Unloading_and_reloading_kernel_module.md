---
title: "Unloading and reloading kernel module"
date: 2012-08-13
forum: General Help
---

### Post by bchurchill on 2012-08-13
Hi all,

I got this wireless card working in a laptop:

Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

When I boot the system, all the modules that need to be loaded are there.  However, the wireless doesn't start working until I

```

#modprobe -r b43
#modprobe b43

```On one occasion I ran lsmod before and after these commands, and found the list of loaded modules was the same.  So, I'm really not sure what is changing when I remove and reinsert b43.  Any ideas on what to look for?  Ideally I would like to setup the kernel to load the right modules in the first place.  However, I wouldn't be too opposed to the hackish solution of running the modprobe commands in a startup script.  What script would be appropriate for this?

---

### Post by bchurchill on 2012-08-14
...bump.  Is there any more information I should provide?

---

