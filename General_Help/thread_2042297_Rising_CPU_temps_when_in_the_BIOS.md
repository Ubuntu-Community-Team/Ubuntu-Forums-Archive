---
title: "Rising CPU temps when in the BIOS"
date: 2012-08-14
forum: General Help
---

### Post by Mazate on 2012-08-14
Does anyone know why when I go into the BIOS settings on my motherboard, the CPU temp slowly rises.  It goes from 38 degrees up to about 50 in a matter of about 30 seconds or so.  It's weird and I've noticed before on other computers I've had, just curious to know if anyone knows why that is.

---

### Post by Aubergines on 2012-08-14
Because at BIOS, the CPU is run at full speed. It's pretty normal

---

### Post by Mazate on 2012-08-14
> **Aubergines said:**
> Because at BIOS, the CPU is run at full speed. It's pretty normal

Why does the CPU run at full speed in the BIOS?  Why would that be necessary?

---

### Post by efflandt on 2012-08-14
Unless it is a laptop or something, usually BIOS is set to let the operating system control cpu speed, etc., but when you are in CMOS setup, there is no operating system, so everything including video would usually be running full speed.

Some Dell laptops will run at reduced speed if they "think" an inadequate power supply is connected (like 65W for one that would usually use 90W), but that is an exception.

---

### Post by idoitprone on 2012-08-14
> **Mazate said:**
> Why does the CPU run at full speed in the BIOS?  Why would that be necessary?

Ack, dymantically using cpu resources is a job of the operating system.

If you do not want to run it at full speed, then you literally have to run a operating system in the bios. We already suffer enough from all major operating system. It will be painful just like uefi specs

---

### Post by SteveHillier on 2012-08-14
THe other week I was called to a machine that I supplied about 2 years ago which was having problems, shutting down unexpectedly - all indicative of CPU overheating.
I opened the box expecting to see a mat of dust, s..t & corruption over the heat sink but it was clean.
I looked at the CPU temperature in BIOS and it was showing nearly 70 degrees.
Against all common sense - the CPU being fitted with one of the grey heat sink mats when new - I removed the processor, added some heat sink paste and re-ran it.  CPU temperature settled at around 30 degrees.
Maybe, just maybe.  You never know!!

---

### Post by idoitprone on 2012-08-14
> **SteveHillier said:**
> THe other week I was called to a machine that I supplied about 2 years ago which was having problems, shutting down unexpectedly - all indicative of CPU overheating.
I opened the box expecting to see a mat of dust, s..t & corruption over the heat sink but it was clean.
I looked at the CPU temperature in BIOS and it was showing nearly 70 degrees.
Against all common sense - the CPU being fitted with one of the grey heat sink mats when new - I removed the processor, added some heat sink paste and re-ran it.  CPU temperature settled at around 30 degrees.
Maybe, just maybe.  You never know!!

paste is more efficient at removing heat than pads

---

### Post by dcstar on 2012-08-15
> **idoitprone said:**
> paste is more efficient at removing heat than pads

Paste can dry out and lose thermal conductivity, so can pads.

Time will slowly degrade all thermal conductivity as dust clogs things, fan bearings wear out and problems like above occur.

---

