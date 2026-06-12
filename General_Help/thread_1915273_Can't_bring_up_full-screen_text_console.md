---
title: "Can't bring up full-screen text console"
date: 2012-01-25
forum: General Help
---

### Post by bkline on 2012-01-25
On one of my Xubuntu workstations I am no longer able to switch from the GUI to the text-based console (Control+Alt+F1/F2, etc).  No idea what caused it.  Any clues about where to start for diagnosing and fixing this?

Thanks!

---

### Post by gsgleason on 2012-01-25
Do you still have /etc/init/tty[1-6].conf

---

### Post by bkline on 2012-01-26
> **gsgleason said:**
> Do you still have /etc/init/tty[1-6].conf

Yes.  Same content, owner (root) and permissions as on the other system, none of which have the problem.

---

### Post by bkline on 2012-01-29
To be more specific: when I press Ctrl-Alt-F[1-6] the monitor behaves as if it has no input at all; the screen is blank except for the floating box the hardware displays saying what the preferred resolution is.  I can get the GUI back with Ctrl-Alt-F7 (but with "sudo init 1" the GUI goes away and the system is hung -- I've waited hours -- in the same state described above until I turn off the power).

I can't see anything in the system log, or any difference in the configuration between this box and the ones that work correctly.  Surely there must be a log somewhere that would provide me some clues.  Any suggestions?

---

### Post by bkline on 2012-01-30
OK, perhaps this isn't the right forum.  Can some kind soul direct me to a group that really knows how the tty software works: what components are involved, how to enable more logging of failures, or find existing log files that might be tucked away somewhere other than in /var/log, etc.?  I really want to get this run to ground.

---

### Post by bkline on 2012-02-01
> **bkline said:**
> OK, perhaps this isn't the right forum.  Can some kind soul direct me to a group that really knows how the tty software works: what components are involved, how to enable more logging of failures, or find existing log files that might be tucked away somewhere other than in /var/log, etc.?  I really want to get this run to ground.

Please!?! :-)

---

### Post by pbrane on 2012-02-01
Are you running a custom kernel?

---

### Post by bkline on 2012-02-01
> **pbrane said:**
> Are you running a custom kernel?

Thanks for the response.  No, it's the stock 3.0.0-15-generic that comes by default with the current Ubuntu.  Any suggestions on where I should be sleuthing?

---

### Post by pbrane on 2012-02-01
Not really, sorry. I am using xubuntu 11.10 and I recently installed a custom kernel (3.2.2) and didn't enable VESA framebuffer support. This will cause the same trouble you are having. Now I'm rebulding the kernel. Have you rebooted? Have you tried an earlier kernel version? 3.0.0-14 may still be present if you haven't removed it as 3.0.0-15 is an update.

One more thing, if you look at dmesg output and grep for vesafb you should see some entries near the end of the boot log. Maybe there will be some info there that will be useful.
```

dmesg | grep -in vesafb

```

---

### Post by bkline on 2012-02-01
> **pbrane said:**
> Have you rebooted?

Many times. :-)

> **pbrane said:**
> Have you tried an earlier kernel version?

Yes, didn't help.

> **pbrane said:**
> One more thing, if you look at dmesg output and grep for vesafb you should see some entries near the end of the boot log. Maybe there will be some info there that will be useful.
```

dmesg | grep -in vesafb

```

Bingo!  Somehow the fb mode had been set way too high.  Don't see how it happened (there was nothing in the grub files setting the mode explicitly to anything, as far as I could tell), but as soon as I put the explicit mode settings into the boot process the problem was solved.

Thank you, thank you, thank you!!!

---

