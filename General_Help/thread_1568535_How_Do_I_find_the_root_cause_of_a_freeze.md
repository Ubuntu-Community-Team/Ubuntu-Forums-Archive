---
title: "How Do I find the root cause of a freeze?"
date: 2010-09-05
forum: General Help
---

### Post by rebornglobe on 2010-09-05
Hi Fellow Ubuntu users,

I am running Ubuntu 10.04 x64 with the following specs:

Kernel 2.6.32-25-generic
Inspiron 1420
Intel Core 2 Duo T550
4 GB RAM
Intel X3100 / 965 GMA Video Card

I've already enabled apport however it isn't able to capture any causes for the random freeze of my system.  I've encountered a number of freezes for no apparent reason and the sad part is Ctrl + Alt + Backspace also does not work (even though I've already enabled it)

Any ideas on where to look and possibly how to solve it?

Thanks

---

### Post by sideburns on 2010-09-05
I don't know if it's related, but my sister's Ubuntu box has frozen twice in the last hour, requiring reboots both times.

I was able to use Ctrl-Alt-F2 to get to a terminal, use top to find that various projects on boinc were using almost all of her CPU time and kill them, but it didn't help.  In the second case, I killed Xorg hoping that this would get it unwedged; she was able to log in again but had no mouse, so we ended up rebooting anyway.

I'm putting this here for two reasons: one, it legitimately bumps the thread and two, any trouble-shooting suggestions will probably be relevant for both of us.  If it turns out our freezes aren't related, I'll start a new thread for mine once I've got an idea of what's causing it.

---

### Post by dirghrabadia on 2010-09-05
I too had freezes occasionally, when I hibernated the system.

---

