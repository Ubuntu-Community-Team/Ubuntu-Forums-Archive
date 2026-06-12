---
title: "memory editor for ubuntu"
date: 2009-10-30
forum: General Help
---

### Post by gft55827 on 2009-10-30
hello, im a new user. i hope ill get some help from you.
I need a memory reader and possibly writer for linux.

something like winhex from windows.
dont need gui, i can live with just dumped data to .txt with SAVED offsets.
i want to attach it to other process and read its memory. please, tell me what to use.

---

### Post by grizato on 2009-10-30
Sorry, this one is GUI but it's the best one I know: gparted

I hope that's what you want unless you mean something like Disk Usage Analiser

---

### Post by lavinog on 2009-10-30
> **gft55827 said:**
> hello, im a new user. i hope ill get some help from you.
I need a memory reader and possibly writer for linux.

something like winhex from windows.
dont need gui, i can live with just dumped data to .txt with SAVED offsets.
i want to attach it to other process and read its memory. please, tell me what to use.

You are referring to ram and not disk storage, correct?

---

### Post by gft55827 on 2009-10-31
u got it wrong.

i really dont know why for all of you memory = hd. whatever, i dont want this topic closed, so i give you a hint:

Reading /proc/pid/mem using data from /proc/pid/maps is what i need. /and why its so lame, cant maps be in any normal way? i hate aprsing txt! it sucks./
i can write program myself, but i would prefer ready one.


or maybe you dont know what is virtual memory?


physical memory = RAM, access from 0 to its limit.
virtual memory = memory used by process. its translated to RAM before accessing.

---

### Post by lavinog on 2009-10-31
pmap [pid] lets you view the map

I don't see anything that lets you edit the memory though, you might have to write your own program.
/dev/mem would more likely what you want to use.

[http://publib.boulder.ibm.com/infocenter/systems/index.jsp?topic=/com.ibm.aix.files/doc/aixfiles/mem.htm](http://publib.boulder.ibm.com/infocenter/systems/index.jsp?topic=/com.ibm.aix.files/doc/aixfiles/mem.htm)

---

### Post by gft55827 on 2009-10-31
dev mem is only for process opening it.

---

### Post by mc4man on 2009-10-31
search hex in synaptic and see if any suit your needs, probably a dozen or so packages of varying capabilities interspersed in the search results

---

### Post by wildweathel on 2009-10-31
It sounds like what you're looking for are "core files."  A core file is a binary snapshot of a process's virtual memory along with a memory-map.  Ubuntu uses the [ELF format]("http://en.wikipedia.org/wiki/Executable_and_Linkable_Format") for core dumps, libraries, executables, object code, etc.  There are plenty of tools for manipulating these, but I'd start out by looking at the [GNU Debugger]("http://sourceware.org/gdb/current/onlinedocs/gdb_toc.html#SEC_Contents") (part of the Ubuntu base install), which can connect to processes, manipulate their memory, take core dumps, inspect core dumps, etc, etc.  

Also, [GNU binutils]("http://www.gnu.org/software/binutils/") (again, part of the Ubuntu base install) is the toolset for taking apart non-running programs and coredumps: (dis)assembly, examining memory maps, listing symbols, etc, etc.  

Basically, gdb for live processes, binutils for dead files.

That said, I'm kinda shooting in the dark.  Maybe if we know why you need to poke around the vm of a process we can give a more helpful answer of how to do what you're trying to do.

---

### Post by gft55827 on 2009-11-01
yes core dump is what i want.
i want to search data in memory of process, and replace it by my own. Or just get the address, so i can ptrace_pokedata from my own program.


how do i core dump using gdb?

---

### Post by gft55827 on 2009-11-02
bump

---

