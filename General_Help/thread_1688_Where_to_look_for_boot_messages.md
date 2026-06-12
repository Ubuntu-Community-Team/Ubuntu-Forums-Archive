---
title: "Where to look for boot messages"
date: 2004-10-22
forum: General Help
---

### Post by salmankhilji on 2004-10-22
While my computer boots, modprobe has some fatal errors right after it loads the hotplug stuff.  Before I can post the exact error message, where do I look for that error message in the log files?

I did a grep in /var/log/ directory, but it came with empty results.

---

### Post by iarwaith on 2004-10-22
Try running 
```
dmesg &gt; file.txt; more file.txt
```

I'm not on a *nix machine to see if it gives modprobe info, but it's always helped me.

---

### Post by oohlaf on 2004-10-23
Or just pipe dmesg directly to your pager:

```
dmesg | pager
```

During boot you can press F2 to see all the boot messages.

---

### Post by butters on 2004-10-23
I bet you have a Dell laptop and your fatal modprobe errors involve loading the hardware random number generator modules, which don't work properly due to Dell's crappy BIOS.  Don't worry about those, the linux kernel can generate pseudorandom numbers in software.  I recompiled my kernel and removed the hw_random modules, but don't recompile your kernel just to avoid warning messages (at least get rid of the hundreds of other modules in the default kernel that you will never have hardware for).

---

