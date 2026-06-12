---
title: "How to use faumachine?"
date: 2011-03-22
forum: General Help
---

### Post by qiet72 on 2011-03-22
Hi,

Has anybody experimented with faumachine - a virtual machine emulator similiar to qemu?  I am trying to get something up and running with faumachine.  I downloaded a mini.iso of Ubuntu Maverick and I would like to install Ubuntu Maverick using mini.iso under faumachine.

Any ideas how?  I played with the gui by running faum but i cannot figure out how to make it use and boot from my iso file.  It looks like it is using vhdl files for configuration files.  I tried google searching but the documentation is very sparse.

qiet72

---

### Post by idoitprone on 2011-03-22
virtualbox or vmware are options?

---

### Post by qiet72 on 2011-03-23
Vmware and virtualbox I use already, but I cannot use them to inject virtual hardware errors into the virtual machine.  For example, if I run memtest86 in the virtual machine, I want to provoke memtest86 by injecting a memory error.  faumachine is the only virtual machine software that I know of that can do that.  It can also inject bad sectors on a virtual hard disk.

Do you know of any other virtual machine software that can do this?

qiet72

---

### Post by qiet72 on 2011-03-23
My goal is for testing how various file systems and raid systems deal with bad sectors popping up from hard drives.  This is hard to do with real hardware but faumachine can do it virtually.  I know some people just use dd command to corrupt a file system but that is not the same thing.

qiet72

---

