---
title: "Problem in applying patch"
date: 2011-07-21
forum: General Help
---

### Post by Annie4ka on 2011-07-21
I was trying to install [COLOR=Blue][**pH-uti**l]("http://people.scs.carleton.ca/%7Emvvelzen/pH/pH.html").[/COLOR] For this purpose i need to patch linux kernel by[COLOR=Blue][ **this**]("http://people.scs.carleton.ca/%7Emvvelzen/pH/pH-0.30.1.diff").[/COLOR]
My linux kernel version is linux-2.6.31-14-generic.
I changed my current directory for /usr/src/linux-2.6.31-14-generic and run command
sudo git apply pH-0.30.1.diff 

So, I get this:
[I][B]annie4ka@annie4ka-desktop:/usr/src/linux-2.6.31-14-generic$ sudo git apply pH-0.30.1.diff
pH-0.30.1.diff:191: trailing whitespace.
#define PH_COUNT_PAGE_MAX (PAGE_SIZE / PH_NUM_SYSCALLS) 
pH-0.30.1.diff:472: trailing whitespace.
    
pH-0.30.1.diff:490: trailing whitespace.
    
pH-0.30.1.diff:545: trailing whitespace.
    
pH-0.30.1.diff:625: trailing whitespace.
    
error: patch failed: Makefile:1
error: Makefile: patch does not apply
error: patch failed: arch/x86/kernel/entry_32.S:336
error: arch/x86/kernel/entry_32.S: patch does not apply
error: patch failed: arch/x86/kernel/process_32.c:727
error: arch/x86/kernel/process_32.c: patch does not apply
error: patch failed: fs/exec.c:60
error: fs/exec.c: patch does not apply
error: patch failed: fs/nfs/super.c:1718
error: fs/nfs/super.c: patch does not apply
error: include/asm-x86/unistd_32.h: No such file or directory
error: patch failed: include/linux/sched.h:88
error: include/linux/sched.h: patch does not apply
error: patch failed: kernel/exit.c:47
error: kernel/exit.c: patch does not apply
error: patch failed: kernel/fork.c:56
error: kernel/fork.c: patch does not apply
error: patch failed: security/Kconfig:115
error: security/Kconfig: patch does not apply
error: patch failed: security/Makefile:16
error: security/Makefile: patch does not apply[/B]



If somebody knows how to fix it, please help!
Thank you[/I]

---

