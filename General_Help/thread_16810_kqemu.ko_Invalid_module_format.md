---
title: "kqemu.ko: Invalid module format"
date: 2005-02-24
forum: General Help
---

### Post by sleepyhead on 2005-02-24
I've compiled and installed the CVS snapshot of the qemu emulator (the basis for the new Win4Lin product), along with the kqemu kernel module. Everything compiled without incident. However, when I try to load the kqemu module, I get the error:

FATAL: Error inserting kqemu (/lib/modules/2.6.8.1-5-686/misc/kqemu.ko): Invalid module format

From what I can google, this seems to indicate that the module was compiled against the wrong kernel sources. uname -r shows 2.6.8.1-5-686 and the only sources I have are in /usr/src/linux-source-2.6.8.1

I installed the kernel source using synaptic (running Ubuntu Warty). Are these the
wrong kernel sources? Do I need to find different kernel sources, and recompile the
kqemu module?

Thanks!

---

### Post by FFL on 2005-04-06
Same problem here. Any suggestions?
Only difference is that I use Hoary ("unstable") with stock kernel  ```
2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux
```

 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux

---

### Post by lachmacn on 2005-06-24
[http://ubuntuforums.org/showthread.php?t=39513&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=39513&page=1&pp=10)

Have a look at this.  It might help.  It uses the linux-headers as opposed to the linux-source.  Worked for me.

---

### Post by weijie90 on 2005-09-25
help pls.. it didnt work for me. im using linux-headers...

---

