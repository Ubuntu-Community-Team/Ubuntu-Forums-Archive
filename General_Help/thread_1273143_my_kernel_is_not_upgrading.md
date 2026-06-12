---
title: "my kernel is not upgrading?"
date: 2009-09-23
forum: General Help
---

### Post by abhilashm86 on 2009-09-23
as you see its not latest kernel, usually before kernel used to upgrade via update manager, it used to invoke, but why its not upgrading?
i use hardy heron 32-bit ubuntu.........
```
abhilash@abhilash:~$ uname -r
2.6.24-23-generic
abhilash@abhilash:~$ 

```

---

### Post by scragar on 2009-09-23
Kernel upgrades require a restart. Very little else will require an update though(The only reason the kernel requires a restart is because it's the very core of your OS, everything else can be unloaded then reloaded).

---

### Post by abhilashm86 on 2009-09-23
> **scragar said:**
> Kernel upgrades require a restart. Very little else will require an update though(The only reason the kernel requires a restart is because it's the very core of your OS, everything else can be unloaded then reloaded).

i daily restart or shutdown also, but my kernel is not automatically upgrading? what is the problem?

---

### Post by abhilashm86 on 2009-09-23
bump!! help needed......

---

### Post by wojox on 2009-09-23
So it won't update to 2.6.24-24 ?

---

### Post by abhilashm86 on 2009-09-23
> **wojox said:**
> So it won't update to 2.6.24-24 ?

no wojox, question is should i compile kernel manually or why my update manager is not showing a new kernel is available for upgrade??

---

### Post by abhilashm86 on 2009-09-23
[according to this]("http://www.kernel.org/"),stable kernel is almost 2.6.24-31, but mine is just 2.6.24-23, so is there any error with update manager??

---

### Post by wojox on 2009-09-23
I don't know ? Hardy's kernel is ready: [https://launchpad.net/ubuntu/hardy/+source/linux/2.6.24-24.60](https://launchpad.net/ubuntu/hardy/+source/linux/2.6.24-24.60)

---

### Post by wojox on 2009-09-23
Oh that thread. You'll have to compile manually for that version.

---

### Post by abhilashm86 on 2009-09-23
its really sad that, hardy being till 2011, not including most of updates?? these things should be done by update managers or atleast syaptic, ok anyways fine, i'l learn compiling a kernel!! wooh

---

### Post by sanket_s on 2009-09-28
Same problem here, in interpid. Still using 2.6.24-19 having downloaded and restarted many later versions from update manager, but not using. I tried changing /boot/grub/menu.lst to use the new kernel but still it gets the backup file and boots into that. When i tried removing the back-up file, it din boot only. I had to restore the file manually from outside ubuntu then. HELP!!! :confused:

Ok, it solved with a upgrade to 9.10... though even today i have to edit menu.lst manually to use the newer kernels... keeps the grub menu simple and to ur needs...

---

