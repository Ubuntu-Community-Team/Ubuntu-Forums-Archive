---
title: "os will not load"
date: 2011-07-21
forum: General Help
---

### Post by rhythmiccycle on 2011-07-21
all of a sudden when I try to boot I get a screen thats says 
```

BusyBox v1.17.1 (ubuntu 1:1.17.1-1ubuntu) Built-in Shell (ash)

Enter 'help' for List of built-in commands

(initramfs)

```

---

### Post by Bucky Ball on 2011-07-21
Do you then get a cursor to log in? If so, type this in:

startx

---

### Post by jocko on 2011-07-21
> **Bucky Ball said:**
> Do you then get a cursor to log in? If so, type this in:

startx
You can't start x from busybox. As far as I know busybox loads directly from the initial ramdisk (initramfs), as a fallback when something very central fails in the early boot process (such as mounting the root file system).

rhythmiccycle: are there any error messages before you are dropped to busybox?

---

### Post by rhythmiccycle on 2011-07-21
i typed "startx" and it said command not found

i tried to cat /bin/sh to see whats in there, and I say nonsense, then didn't know how to exit, so I hit the power button on my pc, then all of a sudden the desktop loaded.

I don't understand what happened, but I'm back in somehow, but I'm scared to reboot.

---

### Post by 2F4U on 2011-07-21
You should check the system log files whether they contain any hint on why the boot process failed.

---

