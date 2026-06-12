---
title: "llseek compilation problem"
date: 2011-02-28
forum: General Help
---

### Post by egunadi on 2011-02-28
I recently upgrade my workstation to Ubuntu. However, some of my program (that used to compile fine on Fedora) now face compilation problem due to missing lib. The error is as follow. I have included sys/types.h and unistd.h. What library / package am I missing?

To avoid confusion, syscall.cc is one of the file in my program, not at all syscall.cc of the system. The program is a system simulator.

syscall.cc:38: error: ?_llseek? has not been declared
syscall.cc:38: error: ?fd? has not been declared
syscall.cc:38: error: ?offset_high? has not been declared
syscall.cc:38: error: ?offset_low? has not been declared
syscall.cc:38: error: ?result? has not been declared
syscall.cc:38: error: ?whence? has not been declared
syscall.cc:38: error: expected constructor, destructor, or type conversion before ?;? token
syscall.cc: In member function ?void X86_CPU_C::intercept_syscall_for_x86vm(x86Instruction_c*)?:
syscall.cc:169: error: ?_llseek? was not declared in this scope

---

