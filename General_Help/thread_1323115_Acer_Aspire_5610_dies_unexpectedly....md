---
title: "Acer Aspire 5610 dies unexpectedly..."
date: 2009-11-11
forum: General Help
---

### Post by gjatute on 2009-11-11
Hello people! After three years (or so) of respectable work today my laptop (one of my) started to die unexpectedly (it died three times already and it's kind of scaring...). Why am I posting here? Because between yesterday and today I have been upgrading from Ubuntu 8.04 to 9.10. Now, I realize it's unlikely (probably impossible) that this is the cause, it looks like an hardware problem, of course. But... It's a bit weird, no?? :confused:

In any case I have no idea about how to solve the problem (if not solving at least facing ](*,)). Suggestions are welcome :frown:

---

### Post by John Bean on 2009-11-11
> **gjatute said:**
> But... It's a bit weird, no??
Not really. Stuff happens, especially with old hardware.

> In any case I have no idea about how to solve the problem (if not solving at least facing ](*,)). Suggestions are welcome :frown:I have no idea what you're asking, since you haven't actually described the problem.

---

### Post by gjatute on 2009-11-11
> **John Bean said:**
> Not really. Stuff happens, especially with old hardware.

I have no idea what you're asking, since you haven't actually described the problem.

What I'm asking is: is there something I can do to find out why it started to die? Is it really possible that the problem arose because of the upgrades? And so on...

---

### Post by niccolo.cascarano on 2009-11-24
I have the same problem on the laptop of a friend of mine.
She has an ASPIRE 5610 and after the upgrade to Karmic koala her laptop started to die suddenly.

I digged in the kernel log and seems that the problem is related to an ACPI event.

```
kernel: [ 6864.809053] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] 20090521 evregion-424
kernel: [ 6864.809075] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.WMID.Z000] (Node f70118b8), AE_TIME
kernel: [ 6864.809120] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.WMID.WMBA] (Node f7011ae0), AE_TIME
```


I tried to disable the ACPI support (adding noacpi on the boot parameters) but it did not solved the problem.

Does anybody know a fix for this?

---

### Post by gjatute on 2010-01-19
I finally solved the problem with a fresh installation. Now Karmic Koala is happily running and the computer doesn't die anymore!

---

### Post by jtpoole99 on 2010-04-22
I have an Acer Aspire 5610 and since installing Ubuntu 9.10, the computer tends to shutdown by itself while I'm using it.  Does this happen to anyone else?  I would like to know what's causing this so I can either fix/solve it.  I never had this problem on 9.04, 8.10 or 8.04.  Any help in solving this problem would be appreciated.

---

### Post by auspex on 2010-05-06
Damn that's annoying.  I have a 5730 and the same thing is happening.  It's condescending to suggest that these things happen "on old hardware" - my hardware is a year old - but I imagine it's using the same DSDT as the 5610s.

I would imagine that the problem is overheating.  When ACPI dies, the thermo sensors are showing 0C, the fan doesn't come on, and when it heats up too much, everything shuts down.  In my case, it never got to the point of shutting down, but I couldn't reboot next morning.  Had to remove the battery and leave it unplugged for a few hours.

My best suggestion is use a different kernel - I'm going right back to my Karmic kernel.

---

