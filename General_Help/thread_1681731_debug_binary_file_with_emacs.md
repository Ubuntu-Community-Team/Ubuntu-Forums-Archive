---
title: "debug binary file with emacs"
date: 2011-02-04
forum: General Help
---

### Post by erjoalgo on 2011-02-04
Hi all, 
Although my problem is very specific, I pose a general question which answer will help my specific issue.

I am debugging a source code in C, using gdb through an emacs buffer.
Using 2 buffers, Emacs has the very nice feature of displaying breakpoints set in gdb to their corresponding line in the source code buffer. It also displays a moving arrow as the instructions are stepped through in gdb, which makes debugging much less tedius and more efficient.

How can I do this for library function calls, for which no source code is available?
In particular, I would like to step through the disassembled binary in GDB and have emacs point to the 
machine instruction being executed in something like the objdumb of the binary. 

This would save me lot of tedious work having to lookup the current gdb instruction.
Has anyone achieved this? Any ideas on how to efficiently debug a binary?

ANY inputs are appreciated. Thanks

---

### Post by kakk on 2011-02-07
Hi,
not an expert on gdb, but have used it a little. I'm afraid you can't debug libraries which have been compiled without the -g option, in addition all kind of optimizations make debugging much more difficult. Some libraries on ubuntu repositories provide the -gdb additional package, which may be what you are looking for.

---

### Post by erjoalgo on 2011-02-09
Thanks for your reply,
I am simply stepping through the assembly instructions in GDB, I have 0 source code. I would just like emacs to display a pointer on the corresponding disassembled instruction. 
This surely exists, and otherwise it would not be hard to implement compared to the similar feature corresponding to source code.
Has anyone tried to step through disassembly instructions within emacs?
Any ideas are welcome. 
Thanks

---

### Post by nickrob on 2011-02-10
From the menu bar: GUD -> GDB-Frames -> Disassembly displays the individual instructions where you can set, toggle and remove breakpoints in the margin and step as for the source.  The info manual describes all this and more. If you have the toolbar enabled (generally useless but handy for debugging) you can click on the help icon on the right to go straight to the relevant section in the manual. A link on my home page shows a screenshot of Emacs 23.1 debugging assembler source code.

---

