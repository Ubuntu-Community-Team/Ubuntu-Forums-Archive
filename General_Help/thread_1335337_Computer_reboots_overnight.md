---
title: "Computer reboots overnight"
date: 2009-11-23
forum: General Help
---

### Post by txtinman on 2009-11-23
I'm running Ubuntu 9.10 and my computer has started to reboot overnight. In a previous thread someone suggested looking in the log files at /var/log. There must be 30+ files there. Could someone narrow it down a bit for me? I doubt I'll know what the problem is even if I see it, but I'll give it a try anyway.

Mike White

---

### Post by Sam on 2009-11-23
Check the files /var/log/dmesg, /var/log/messages or /var/log/syslog.
Is there something in /var/crash ?

---

### Post by oldsoundguy on 2009-11-23
You could also be experiencing a power blip (quick off and then back on)  OR there could be a hardware issue .. I have a Mythbuntu (9.04) box that reboots for no damn reason when it sits at idle too long.  (It lives on a UPS) I suspect it is a hardware issue, but the temp monitor NEVER fires off an alarm, so not the processor per se.

Easy way to check the power is to put a digital clock on the same outlet .. if it is flashing after the re-boot, you have a power problem.

---

### Post by txtinman on 2009-11-23
> **Sam said:**
> Check the files /var/log/dmesg, /var/log/messages or /var/log/syslog.
Is there something in /var/crash ?
There was nothing in /var/crash and I can't make heads or tails out of the other log files. I can see where the reboot happened, but I can't tell what caused it. I did a manual reboot and compared the messages. They look identical.

Mike White

---

### Post by kestrel1 on 2009-11-23
You could have a memory stick that is going bad & is causing this or even the PSU. I would try swapping out the memory & see if that helps.

---

### Post by lisati on 2009-11-23
Perhaps I've been using Windows too much lately, but my first thought was of automatic updates. Then I remembered that Ubuntu handles updates differently.......

---

### Post by doas777 on 2009-11-23
> **kestrel1 said:**
> You could have a memory stick that is going bad & is causing this or even the PSU. I would try swapping out the memory & see if that helps.

or just test them with memtest86

---

