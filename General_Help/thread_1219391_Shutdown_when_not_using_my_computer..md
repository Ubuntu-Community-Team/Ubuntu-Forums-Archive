---
title: "Shutdown when not using my computer."
date: 2009-07-21
forum: General Help
---

### Post by Salvador Linux on 2009-07-21
Hello, my computer shutdowns when i am not using it.
Does anyone know how to solve this?
I am using Ubuntu 9.04 with an ASUS M2nmxse motherboard (which have an ACPI bug at startup).
Thanks.

---

### Post by LowSky on 2009-07-21
go to power management under system > administration

make sure the PC doesn't go to sleep after a certain time limit

---

### Post by Janeway on 2009-07-21
Hi,

do you mean that your computer shuts down when you do not use it for some time or that you want it to do that?

However, under System >> Prefernces >> Screensaver you can choose an Action on inactive time. There you can enable and disable the shutdown event.

Regsrds
Janeway

---

### Post by Salvador Linux on 2009-07-21
> **LowSky said:**
> go to power management under system > administration

make sure the PC doesn't go to sleep after a certain time limit

> **Janeway said:**
> Hi,

do you mean that your computer shuts down when you do not use it for some time or that you want it to do that?

However, under System >> Prefernces >> Screensaver you can choose an Action on inactive time. There you can enable and disable the shutdown event.

Regsrds
Janeway

I have checked that setting and it is set at to never sleep when an amount of time is reached when the computer is inactive by default.
I want my computer to not shutdown when i am not using it.

---

### Post by PGScooter on 2009-07-21
I think you're going to need to post the output of ```
sudo dmesg
```. When you do so, indicate whether your last shutdown was a normal shutdown (ie, you chose to shut it down) or an unwanted shutdown. If it was a normal shutdown, what was the one before that? It would be helpful for you to indicate which shutdown (the third one back) was the unwanted one.

Have you watched it shutdown by itself? It probably wouldn't be too much fun, but could be useful. It is probably helpful to know if it crashes (ie just turns off all of a sudden) or if it shutsdown as if a ghost shut it down.. hm... maybe that's what's happening. Any ghosts in your house?

---

