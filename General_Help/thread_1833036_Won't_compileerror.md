---
title: "Won't compile/error"
date: 2011-08-25
forum: General Help
---

### Post by Theredbaron1834 on 2011-08-25
I am trying to compile [this]("http://theredbaron.site90.com/Baron_Stuff/eee.c") kernel module on ubuntu 11.04 with linux 2.6.38. However, I keep getting errors.
```
theredbaron@theredbaron-900:~/Downloads/eeepc-linux/module$ make
make -C /lib/modules/2.6.38-11-generic/build M=/home/theredbaron/Downloads/eeepc-linux/module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /home/theredbaron/Downloads/eeepc-linux/module/eee.o
/home/theredbaron/Downloads/eeepc-linux/module/eee.c: In function ‘eee_proc_init’:
/home/theredbaron/Downloads/eeepc-linux/module/eee.c:399:43: error: ‘proc_root’ undeclared (first use in this function)
/home/theredbaron/Downloads/eeepc-linux/module/eee.c:399:43: note: each undeclared identifier is reported only once for each function it appears in
/home/theredbaron/Downloads/eeepc-linux/module/eee.c:404:21: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/theredbaron/Downloads/eeepc-linux/module/eee.c:421:18: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/theredbaron/Downloads/eeepc-linux/module/eee.c: In function ‘eee_proc_cleanup’:
/home/theredbaron/Downloads/eeepc-linux/module/eee.c:442:31: error: ‘proc_root’ undeclared (first use in this function)
make[2]: *** [/home/theredbaron/Downloads/eeepc-linux/module/eee.o] Error 1
make[1]: *** [_module_/home/theredbaron/Downloads/eeepc-linux/module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make: *** [all] Error 2

```I looked over the code, and it doesn't look that "hard", just too hard for me. Anyone willing too look it over?

---

