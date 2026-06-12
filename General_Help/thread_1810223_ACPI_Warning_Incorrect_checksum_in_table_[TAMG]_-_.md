---
title: "ACPI Warning: Incorrect checksum in table [TAMG] - 0xD6, should be 0xD5"
date: 2011-07-22
forum: General Help
---

### Post by RayVad on 2011-07-22
What does this warning mean? And is this a serious problem?
ACPI Warning: Incorrect checksum in table [TAMG] - 9D, should be 9C (20090903/tbutils-314)


Having problems with GA-X58A-UD3R (rev2.0) It seems stable but got segfaults on some files after a while. Mostly on big files.
Think it is due memory timings(24Gb Geil Value plus memory). Harddisk is already swapped, but no success yet.
Maybe this has something to do with ACPI Warning: Incorrect checksum in table [TAMG] - 9D, should be 9C (20090903/tbutils-314)
?

---

### Post by RayVad on 2011-08-01
Some one who can tell if this warning is normal for newer system boards with 2X 16bit BIOS?

ACPI Warning: Incorrect checksum in table [TAMG] - 0xD6, should be 0xD5

I have a GA-X58A-UD3R with 24Gb of RAM, running Ubuntu 10.04 LTS/11.04 64bit.
Both have the same warning.

---

### Post by blind2314 on 2011-08-01
> **RayVad said:**
> Some one who can tell if this warning is normal for newer system boards with 2X 16bit BIOS?
 
ACPI Warning: Incorrect checksum in table [TAMG] - 0xD6, should be 0xD5
 
I have a GA-X58A-UD3R with 64Gb of RAM, running Ubuntu 10.04 LTS/11.04 64bit.
Both have the same warning.
 
First of all. 64GB of ram on an end-user class mobo?! Jesus. What size DIMMs are you using? 
 
Also, an ACPI warning leads me to believe it's a problem with a harddrive or an external device (including video cards).

---

### Post by RayVad on 2011-08-01
Hi, am using this mobo as Virtualbox server. That's why i did put it max full of RAM 6x4 Gb.
Sorry, wrong writing, meant 24Gb :)

But the warning is ACPI and i think BIOS?
How to find out which device it could be is the question then...

Videocard is swapped from ATI to Nvida, but that is not the one, since the ACPI warning isn't changed.

---

### Post by TechZilla on 2011-12-20
It is actually fairly common, to have some sort of ACPI warning these days!


Its not great, but it should not pose any noticeable problem. If the bug is not in feature critical table, or can be read regardless, it should not have affect.  Many systems I watched boot, have some ACPI warning displayed.  Now when I'm at the data center, or on my workstation (SuperMicro Mobo), The warnings are suspiciously absent. I think the manufacturers put more time into the Server class Motherboard Bios.

Really, it is a bug in your ACPI section of the BIOS.  If it can be fixed with a BIOS update, then I would update.  If The bug is not fixed in an update, I would email the manufacture, as they might not even know.  Remember only a small section use Linux, even less own your board, and even less still would report the error.

---

