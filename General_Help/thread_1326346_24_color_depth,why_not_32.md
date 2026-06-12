---
title: "24 color depth,why not 32?"
date: 2009-11-14
forum: General Help
---

### Post by Romanrp on 2009-11-14
When I used my laptop with windows preinstalled,I was able to have 32bits of color(color depth)
now with ubuntu I can only have 24 bits of color (24 color depth)
I found this on many other distros too.
And yes my graphic card driver is installed and activated..
Is there a way to fix this?
It's not a problem but if it's possible to have a better color depth then why not?

---

### Post by jocko on 2009-11-14
From man xorg.conf:
>        Depth  depth
              This entry specifies what colour depth the Display subsection is
              to be used for.  This entry is usually specified, but it may  be
              omitted to create a match-all Display subsection or when wishing
              to match only against the FbBpp parameter.  The range  of  depth
              values  that  are  allowed  depends on the driver.  Most drivers
              support 8, 15, 16 and 24.  Some also support  1  and/or  4,  and
              some  may support other values (like 30).  Note: depth means the
              number of bits in a pixel that are actually  used  to  determine
              the pixel colour.  32 is not a valid depth value.  Most hardware
              that uses 32 bits per pixel only uses 24 of  them  to  hold  the
              colour information, which means that the colour depth is 24, not
              32.

So there is no "32 bit" color depth.

---

### Post by Romanrp on 2009-11-14
Oh ok.thanks!
Stupid windows for giving false color depth and giving me false hope.

---

