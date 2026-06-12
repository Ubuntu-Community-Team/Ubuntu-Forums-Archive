---
title: "deleting kernels - can I delete this ones?"
date: 2010-10-11
forum: General Help
---

### Post by listerdl on 2010-10-11
Hi I have a dual boot and I know that I can tidy up and remove kernels, i.e. the older ones, from the grub menu but I just would like for you guys to kindly confirm that I am safe to delete these from the system?

My latest install is:

[B]Linux-Headers 2.6.32-25 generic
Linux-Headers 2.6.32-25 generic recovery[/B]

Can I just keep the above 2 - is that what you guys all do?

basically I can delete anything below the current kernel?

Thanks!

[IMG]http://www.georgedalziel.com/Headers1.png"]http://www.georgedalziel.com/Headers1.png[/IMG]

[IMG]http://www.georgedalziel.com/headers2.png"]http://www.georgedalziel.com/headers2.png[/IMG]

---

### Post by dino99 on 2010-10-11
what can happen ?

suppose you only have 1 kernel installed, all is working fine and one day, while updating/upgrading, something break the system (mostly because a video driver is broken and cant built on your kernel)

In that case, if you can boot on a 2d kernel, you are safe, but if you only have your broken one, so you might find the answer yourself, dont you ?

---

### Post by listerdl on 2010-10-11
thanks for that - and your def right....i will keep at least the last two.

problem is that i have like 6 there....

is it safe to delete or remove the e.g.

**linux-headers-2.6.32-24-generic-pae**

Not sure what this pae is?

thanks!

---

### Post by dino99 on 2010-10-11
the 2 latest are enought, both have normal & recovery mode :)

Depend of the ram amount installed on your system, if >= 3 gb, the pae kernel is able to use all the ram, like a 64 bits (with less trouble due to some weird drivers on the 64 side)

On my systems i only install the "generic-pae", not the "generic" at all ( pae might be enabled in bios of course)

---

