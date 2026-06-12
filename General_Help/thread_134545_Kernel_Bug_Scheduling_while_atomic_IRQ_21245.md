---
title: "Kernel Bug: Scheduling while atomic: IRQ 21/245"
date: 2006-02-22
forum: General Help
---

### Post by blindspy on 2006-02-22
I compiled a custom vanilla kernel with a config that I've always used but apparently I've screwed something up and I doesn't boot with this error on Ubuntu:
Bug: Scheduling while atomic: IRQ 21/0x.../245

Same kernel on ArchLinux:
Requesting_Module: Runaway loop modprobe binfmt-464c
and then something like:
irq 21: nobody cared!

Anyone have any hints on how to debug this?

---

