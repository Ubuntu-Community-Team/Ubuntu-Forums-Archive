---
title: "Printing In Firefox help"
date: 2011-10-28
forum: General Help
---

### Post by dardack on 2011-10-28
So I set up the printer to do B&W 600 DPI high quality (it's a laser no color).  If I print where there are blue links, they print really light grey, almost impossible to read.

I want it to print everything black and white, not really grey scale, any help please.

Ubuntu 10.04 LTS, fully updated.

---

### Post by dardack on 2011-10-28
It's a HP laserjet 5si networked printer.

---

### Post by Wayne_V on 2011-10-28
I believe somewhere in the HP driver there is an option for 'print all text as black'.   With high quality it is converting the blue to a grey scale which evidently is not what you want.

---

### Post by dardack on 2011-10-28
> **Wayne_V said:**
> I believe somewhere in the HP driver there is an option for 'print all text as black'.   With high quality it is converting the blue to a grey scale which evidently is not what you want.

Thought so too, but I could not find this option at all.

I ended up using the CUPS driver instead of the HPIJS driver.  The CUPS driver has a color correction option that makes it much more legible.  Not pure black, but way better.

---

