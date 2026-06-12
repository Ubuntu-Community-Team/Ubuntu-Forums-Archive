---
title: "boot failure after upgrade"
date: 2010-09-02
forum: General Help
---

### Post by hockey9876 on 2010-09-02
I recently had my system updated through the automatic updates.
Until then, everything was working wonderful.  Now, I can't
boot, period.  

When I try booting into single user mode, I get an error:
Kernel panic: Unable to mount root fs on unknown block (0,0)
Just prior to that there is a line that said something like
"Here are the available partitions:"  but listed nothing.

The question is what can I do to recover my system without
having to spend hours reinstalling everything?  

I believe the last boot that was good was something
like /boot/vmlinuz-2.6.24-28-generic - I'm not sure how 
to tell which version of the OS it is, but I installed 8.10
way back when...

I've googled the error, but have found nothing that would fix my
problem.  Is there some command I can run at the grub prompt to show find partitions?  One of the suggestions was to boot into
the system using a recovery disk.  The disk I have is the
original install disk.  

I tried booting to the disk into a "recovery mode" but at the
UI install screen, I selected F1 (help) and then F4 recovery
something.  It didn't give me any decent suggestions...

So, here I am...

Appreciate any help out there...  OH, my version of grub is 1.5, not 2 -- at least that's what I see @ boot up before it begins its infinite loop..

Thanks,

John

---

