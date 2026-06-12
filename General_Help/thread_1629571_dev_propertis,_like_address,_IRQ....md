---
title: "/dev propertis, like address, IRQ...?"
date: 2010-11-23
forum: General Help
---

### Post by Cool Javelin on 2010-11-23
Hello hardware gurus:

Is there a way to get hardware specific info about a /dev?

I have added a data acquisition board, and, I don't know if it has shown up in the /dev list, or how to make it do so, or even if I want it to.

It is located at address 0x300, but I don't know how to get that kind of information from something listed in /dev.

I have a program that accesses the board and it is working fine, but I need to run the program as root (sudo acquire_program)

I have been reading about groups and permissions and there may be a way to give access to a /dev/something to a program (or group)

BTW, I have a text only interface, no GUI.

Thanks,
Mark.

---

### Post by Cool Javelin on 2010-12-18
Should I move this to the hardware thread?

Thanks, Mark.

---

