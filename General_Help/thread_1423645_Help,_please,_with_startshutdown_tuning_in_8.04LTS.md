---
title: "Help, please, with start/shutdown tuning in 8.04LTS"
date: 2010-03-06
forum: General Help
---

### Post by hbquikcomjamesl on 2010-03-06
Well, I finally have the box back home. Not quite in its final position, but home from the office at least.

I would like to tune the IPL process, in order to avoid starting (or in some cases attempting to start) anything that is either irrelevant to my hardware, or irrelevant to my environment.

And since the motherboard has APM but not ACPI, I'd like to be able to teach it how to do an APM power-off (it can't be THAT hard; I have a DOS executable that does it, and during the brief time I had RH8 running, it could do it, too.

So far, I've taken the "ACPI=FORCE" out of the boot parameters, and replaced it with NOACPI. I still get a message telling me that the BIOS fails the cutoff date for ACPI support (no duh!), but this at least cleared the second ACPI error message.

Since I don't use Bluetooth, I've gone into "services" on the admin menu, and unchecked it (also unchecked the item that was some sort of ACPI daemon).

Twice in the IPL process I get a message to the effect of "Error inserting battery." Probably because the only battery is a little coin cell for the clock (and maybe the CMOS settings). Where is that coming from, and what is it trying to start.

This box does not have (and most likely never will have) Ethernet; is there anything there I can get rid of, and if so, how?

---

### Post by hbquikcomjamesl on 2010-03-07
Hmm. Adding "noacpi acpi=off apm=on noapic" to the kernel options got rid of the "BIOS fails cutoff date for ACPI" message, where "noacpi" by itself didn't, but still no joy on power-down.

Found this, with an E-series Dell, probably of nearly the same vintage as the D300 whence I salvaged my motherboard:
[http://ubuntuforums.org/showthread.php?t=1046871](http://ubuntuforums.org/showthread.php?t=1046871)
Any comments before I try it?

---

### Post by rnerwein on 2010-03-07
hi
i ain't know if this works during the IPL. but in /etc/defaults/rcS there is a option 
UTC=yes/no - may be this is the reason the for getting the error message:  "Error inserting battery."
just try it may be it works.
ciao

---

### Post by hbquikcomjamesl on 2010-03-07
Hmm "UTC=yes/no" sounds like the option for whether the system TOD clock is treated as UTC or local time (which I changed just this past week, so that the DOS and Linux sides of the box would agree on what time it is without my having to tell Linux it was in Greenwich).

If we're talking about the same option, it has no effect on the "battery" message, or the seeming inability to do an APM power-down.

---

### Post by hbquikcomjamesl on 2010-03-07
No joy with the [http://ubuntuforums.org/showthread.php?t=1046871](http://ubuntuforums.org/showthread.php?t=1046871)
(/sbin/rmmod snd_hda_intel in /etc/default/halt)

I tried [http://ubuntuforums.org/showthread.php?t=2620](http://ubuntuforums.org/showthread.php?t=2620)
(adding "apm" to /etc/modules) Still no joy.

It still stubbornly refuses to cut off the power.

---

### Post by hbquikcomjamesl on 2010-03-07
SUCCESS on the power down:

A little further down, [http://ubuntuforums.org/showthread.php?t=2620](http://ubuntuforums.org/showthread.php?t=2620)
(suggested changing "apm" to "apm power_off=1" in /etc/modules)

THAT WORKED. Once, at least. . . TWICE IN A ROW! I think it's fixed!

---

### Post by hbquikcomjamesl on 2010-03-07
Hmm. Decided to try futzing around with the splash screen again. Found out about it being called "usplash." Found suggestions to try "splash vga=785" and "splash vga=788."

785 produced a black screen, but at least it didn't overdrive the LCD.

788 produced a splash screen, except that it was shifted so far to the right, the right end was appearing on the left side of the screen.

I expected 791 to overdrive the monitor, but it worked. Image is shifted to the right, beyond what the monitor's h-pos and h-size settings could compensate for, but it worked. And it didn't kill the APM shutdown, either.

---

