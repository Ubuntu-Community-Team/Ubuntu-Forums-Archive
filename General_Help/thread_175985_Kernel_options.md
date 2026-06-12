---
title: "Kernel options"
date: 2006-05-14
forum: General Help
---

### Post by ashrack on 2006-05-14
I've always been curious what is the difference if U compile a driver as a module or U compile it in the kernel??

Its my believe that if U compile it in the kernel than the driver is always loaded even if its not needed.
But if U compile it as a module than the driver is initialized when needed. 

Is this correct?

---

### Post by christhemonkey on 2006-05-14
Thats what i thought.

And also i thought modules are built in /lib/modules or something, and drivers built into kernel are part of the kernel image itself?

Thats probably me just being somewhat inexperienced with kernels though...

---

### Post by ashrack on 2006-05-15
[QUOTE=christhemonkey]Thats what i thought.

And also i thought modules are built in /lib/modules or something, and drivers built into kernel are part of the kernel image itself?

Thats probably me just being somewhat inexperienced with kernels though...[/QUOTE]

Is there a downside to compiling stuff in the kernel, and are U still able to unload stuff like sound card which is needed for me in order to hibernate

---

### Post by ashrack on 2006-06-04
[QUOTE=ashrack]Is there a downside to compiling stuff in the kernel, and are U still able to unload stuff like sound card which is needed for me in order to hibernate[/QUOTE]
bump

---

### Post by JohnW on 2006-09-21
I think you didn't get a reply because hibernation simply takes a snapshot of your system's state and has nothing to do with whether something is within the kernel or loaded as a module.

If it's in the kernel it'll occupy memory all the time.  If it's a module it'll load slightly slower, but only be loaded if it's needed.

---

