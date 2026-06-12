---
title: "probs w/ gnome-power-manager, Karmic, AspireOne"
date: 2009-12-11
forum: General Help
---

### Post by mailman1175 on 2009-12-11
Ubuntu 9.10 Netbook Remix on an Acer Aspire One ZG5/AOA110

I've seen several instances of folks who're having problems with their system crashing when they unplug the power cord, but none who're having the same problem I am. That is, the system keeps working, but the gnome-power-manager applet (I think that's what it's called...) doesn't update when the power cord's removed. It shows 100% charge, regardless of condition.

I assume this means, though I haven't tested it, that the computer will just die when the battery runs out, that there will be no warning.

Is this a known bug I haven't been able to find? Is there a workaround? Or do I need to send this in to a bugzilla?

TIA
JM

---

### Post by mailman1175 on 2009-12-14
Nobody's seen this? Off to bugzilla...

---

### Post by mailman1175 on 2009-12-16
So I found lots of bugs at Launchpad that were similar to this one, but none quite like it. One of the workarounds was to install xfce4-power-manager, which I've done.

Here's the thing, though: I put xfce4-power-manager in my Startup Applications, and removed gnome-power-manager from it, but xfce4-power-manager doesn't execute on start-up. I still have to manually execute it. And, every time I fire up Update Manager, it starts gnome-power-manager. It doesn't appear to conflict with xfce4-power-manager, but I kill it anyway, since it doesn't work right.

Does anyone know why xfce4-power-manager's not executing on start-up like I want it to do?

---

### Post by alwa on 2010-01-15
I am running Karmic on a Aspire One 75h and it seems I have a similar problem.
Gnome-power-manager 2.28.1 shows full battery all of the time except if I plug in powercable and then unplug again, then it suddenly starts working (showing correct battery status)??

acpi doesn't seems to report anything either.
I really would prefer not to have to install another power-manager -I would rather find out what the problem is.

Have any of you found a solution to the problem ..or explanation?

---

### Post by mailman1175 on 2010-01-15
> **alwa said:**
> I am running Karmic on a Aspire One 75h and it seems I have a similar problem.
Gnome-power-manager 2.28.1 shows full battery all of the time except if I plug in powercable and then unplug again, then it suddenly starts working (showing correct battery status)??

acpi doesn't seems to report anything either.
I really would prefer not to have to install another power-manager -I would rather find out what the problem is.

Have any of you found a solution to the problem ..or explanation?

I found neither an explanation nor a solution. Even installing xfce4-power-manager was an imperfect solution, but it was better than having the machine just drop dead with no notification (particularly since I was using ext2).

That said, I'm distro-hopping again, so I'm no longer actively searching for a solution to this particular problem.

---

