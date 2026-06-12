---
title: "how to take the snapshot of memory in ubuntu ?"
date: 2010-07-11
forum: General Help
---

### Post by sulekha on 2010-07-11
Hi all,



how to take the snapshot of memory in ubuntu ?
under the following situations :- 

 1) the application crashes
 2) you close it without saving
 3) you save over a doc you had just opened 


 my idea was to do the following

 cp /dev/mem ~/memory.bin

now after copying is done you can access the file using:- less ~/memory.bin
 
but when i tried i am getting this 

root@zodioc:~# cp /dev/mem  ~/memory.bin
cp: reading `/dev/mem': Operation not permitted


 Is there any other way to do this in ubuntu ?

---

### Post by Sylvain Falardeau on 2010-07-11
If you tail -f /var/log/syslog, you will see the following message:

```

kernel: [345599.433480] Program cp tried to access /dev/mem between 100000->108000.

```So it is forbidden to read this section of memory (I don't know why).

If what you want to do is trace a bug in the program you were running when it crashed, the Linux kernel can generate a "core" file for you. The file can be used with "gdb" debugger to analyze the cause.

The core file generation is disabled in Ubuntu. To activate it, use:

```
ulimit -c unlimited
```You will then allow the kernel to generate core files *FOR PROGRAMS CALLED FROM THIS PARTICULAR SHELL ONLY*. If  you start from the menu or another shell, it won't work.

---

