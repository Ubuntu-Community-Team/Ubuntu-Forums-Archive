---
title: "Kworker constant 85% w/ ivy bridge I5"
date: 2012-05-10
forum: General Help
---

### Post by kitchens on 2012-05-10
Just installed 12.04 on a new system with an I5 3550 and a DH67BLB3 motherboard and KWORKER is constantly sitting at around 85% cpu usage. 

Any ideas why that may be?

---

### Post by kitchens on 2012-05-10
Update: I've disabled acpi and that corrected the problem. Still not sure why that would cause this to happen.

---

### Post by freechelmi on 2012-10-11
> **kitchens said:**
> Update: I've disabled acpi and that corrected the problem. Still not sure why that would cause this to happen.


Hi, Just bought this motherboard for Ubuntu 12.04.

Do you still have such issues ?

---

### Post by babixeddu on 2012-12-29
> **kitchens said:**
> Update: I've disabled acpi and that corrected the problem. Still not sure why that would cause this to happen.
Are you sure that disabling acpi solves the problem?

---

### Post by rnerwein on 2012-12-29
> **kitchens said:**
> Just installed 12.04 on a new system with an I5 3550 and a DH67BLB3 motherboard and KWORKER is constantly sitting at around 85% cpu usage. 

Any ideas why that may be?
hi
to disable don't solve the problem it hides only the problem.
about 85% cpu. in wich mode (sys,usr,wait,nice)? i presume in system mod. run top in a terminal to see in which mode it is.
run in a terminal: ps -elf | grep kthread
there you can see in which kernelmodule kthread is running - it's WCHAN
i guess you played with crypted filesystems ???
cheers

---

