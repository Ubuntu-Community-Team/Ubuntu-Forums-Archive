---
title: "System Halt"
date: 2009-08-23
forum: General Help
---

### Post by Super2cool on 2009-08-23
Whenever i try to shutdown my computer I always get this message: 

[52.01502] system halt 

I have tried the sudo shut down now - it does not work 

I have tried apm poweroff=1 - It does not work as i do not have APM [ I have an old computer]

---

### Post by spiderbatdad on 2009-08-23
most of the commands have a related man page. try ```
man shutdown
```you'll see the command requires an option like -h to power off the system. so ```
sudo shutdown -h now
```not sure why it's freezing up. you can try acpi=off or noapic as a kernel option but your battery power monitor, if you have one, probably wont work.

---

