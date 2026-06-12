---
title: "ata8: SRST failed (errno:16)"
date: 2009-10-05
forum: General Help
---

### Post by -=hazard=- on 2009-10-05
Twenty minutes ago I got this error message while booting:
```
ata8: SRST failed (errno:16)
```
I did some search in google and I found out that this was a kernel problem on hardy. I managed to boot successfully by resetting my BIOS settings but anyway I read around that can be done either by unplug/plug the HD switches.
Anyway I just want to know if anybody else had ever got this error and what can be done about that.
```
Ubuntu: 9.04 Jaunty Jackalope
Kernel: 2.6.28-15-generic
```

---

### Post by -=hazard=- on 2009-10-05
No one?

---

### Post by turbotom on 2009-10-19
I get the message on shutdown. Everything works fine, but it takes 5 minutes for the computer to shutdown.

Does it have anything to do with a marvell SATA controller?

---

### Post by LuxAeterna on 2009-10-20
Upon booting today, I get "ata1.00: SRST failed (errno=-16)" written four times, and Ubuntu refuses to boot. Also, I suddenly cannot boot Ubuntu from the live CD anymore. It will give me the before-mentioned error and then show me a BusyBox console.

I did a memory check and it seems to be fine. When booting, it only checks my CD drive for CD's even though BIOS specifically says to check the disk drive first.

My computer has been making some weird sounds the last couple of days. I assumed that a cable had been touching a fan or something similar, but now I am investigating the scenario that my hard disk might have died on me.

If my hard disk crashed, shouldn't the live CD work fine anyway?

---

### Post by manthony121 on 2009-11-02
I have gotten this message when trying, without success, to boot the 9.10 LiveCD on my system with an Intel Mobo with Marvell SATAs.  The attempt to boot hangs with repeating messages about ata6: link slow to respond, and ata6: SRST failed.  It seems there were some issues with Linux support for the Marvell SATA chipset, I don't know if this is still an issue.  I am working on it now.

---

