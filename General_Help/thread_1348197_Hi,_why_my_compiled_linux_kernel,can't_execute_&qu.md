---
title: "Hi, why my compiled linux kernel,can't execute &quot;/init&quot; program from initramfs?"
date: 2009-12-07
forum: General Help
---

### Post by gfz2004xy on 2009-12-07
[SIZE=2]Hi, why my compiled linux kernel,can't execute "/init" program from initramfs?

:p hello, every one! Wish your help.
   I compiled linux kernel 2.6.31, and prepared initramfs, and use the "init"
programme from sysvinit package. 
   kernel and initramfs is made into image.iso, I boot iso in virtualbox.
   
   error: when execute /init program, it blocked a long time(5 mins), then 
        prompt: kernel panic - not syncing: Out of memory and no killable 
        processes... 

   I traced the process, by using printk function, break at 
    kernel_execve syscall, and kernel_execve is not returned.

   the init programme is compiled into static link. I use file command checked.
   when use dynamic link, kernel_execve syscall soon return -2.

   all this happen in init_post() func in $kernel_root/init/main.c  .
   who can give some advices? Thanks a lot.[/SIZE]

---

### Post by JBAlaska on 2009-12-07
I have always had good luck using [KernelCheck](http://ubuntuforums.org/showthread.php?t=618563) to choose options and compile a custom kernel.

[COLOR="Blue"]NOTE: THERE IS A BUG IN KERNELCHECK LUMEN AS DESCRIBED AT:[/COLOR] [https://bugs.launchpad.net/kernelcheck/+bug/432732](https://bugs.launchpad.net/kernelcheck/+bug/432732). [COLOR="Blue"]PATCHING INSTRUCTIONS CAN BE FOUND THERE.[/COLOR]

---

### Post by dcstar on 2009-12-07
> **gfz2004xy said:**
> [SIZE=2]Hi, why my compiled linux kernel,can't execute "/init" program from initramfs?
..........[/SIZE]

It would probably be better to ask in the programming forum, not the general help forum.

---

### Post by gfz2004xy on 2009-12-07
Thanks, I'll try programming forum...

---

