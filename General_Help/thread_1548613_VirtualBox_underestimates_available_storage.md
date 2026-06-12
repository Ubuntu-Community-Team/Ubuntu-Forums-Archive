---
title: "VirtualBox underestimates available storage"
date: 2010-08-08
forum: General Help
---

### Post by Arightwizard on 2010-08-08
Hey,
I'm using VirtualBox OSE to run Windows XP, for watching netflix as well as audio/video editing, and I've assigned it about 3 gb, which it thinks is over 50% of my overall computer's storage when I have about 79 gb left.
Why is it doing this, and how can I get it to "realize" how much memory I actually have?
Thanks,
-Arightwizard

---

### Post by QIII on 2010-08-08
You have a total of 82G of "memory"?  are you running a server?  Or did you mean 8GB?  Also, "storage" is not "memory".

Your virtual machine will be entirely unaware of how much memory and disk is on your physical machine.  It will only know about how much memory and disk space it is assigned.

Say you have 8GB of RAM.  If you assign 3GB to the virtual machine, it will know only about the 3GB.  If you are using 1.5GB for a process, the virtual machine will report that 50% is being used.

If you have assigned the virtual disk 25GB and 15GB is used, the virtual machine will report that you only have 10GB left available on the disk.

Or am I completely misunderstanding your post?

---

### Post by Arightwizard on 2010-08-08
> **QIII said:**
> You have a total of 82G of "memory"?  are you running a server?  Or did you mean 8GB?  Also, "storage" is not "memory".

Your virtual machine will be entirely unaware of how much memory and disk is on your physical machine.  It will only know about how much memory and disk space it is assigned.

Say you have 8GB of RAM.  If you assign 3GB to the virtual machine, it will know only about the 3GB.  If you are using 1.5GB for a process, the virtual machine will report that 50% is being used.

If you have assigned the virtual disk 25GB and 15GB is used, the virtual machine will report that you only have 10GB left available on the disk.

Or am I completely misunderstanding your post?
Actually, I just misunderstood VirtualBox's settings. It was referring to the amount of RAM I gave it, but I thought it meant storage. (When I said "memory" in the last sentence, that was just an example of when I'm not thinking about what I'm typing. Just a mistake)
Marking this thread as resolved now..

---

