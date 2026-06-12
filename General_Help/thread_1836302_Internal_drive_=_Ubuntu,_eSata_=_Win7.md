---
title: "Internal drive = Ubuntu, eSata = Win7"
date: 2011-08-30
forum: General Help
---

### Post by yumgnomeandthensome on 2011-08-30
Hi guys, 
I have a laptop with an internal HDD with Win7 installed. 
I would like to do the following
1/ take out the internal HDD from the laptop and connect it in the future via my eSata port
2/ install a SSD into laptop and install Ubuntu

Result:
Laptop runs one OS, Ubuntu. When I need to boot into Win7, I just connect the HDD via eSata port and boot off this drive.

Is this possible/good design?

regards,
Evan

---

### Post by khaos1985 on 2011-08-30
This is very possible and very easy to do.
 First set your bios to boot to external devices first and then internal devices second.
Then install your ubuntu flavor to the internal device and put the grub on that drive.
And then have the Win7 OS on the external drive with the windows boot loader on the external drive.
Reboot with what ever device you want to then.
:lolflag:

---

### Post by krlosjcc on 2011-09-02
> **khaos1985 said:**
> This is very possible and very easy to do.
 First set your bios to boot to external devices first and then internal devices second.
Then install your ubuntu flavor to the internal device and put the grub on that drive.
And then have the Win7 OS on the external drive with the windows boot loader on the external drive.
Reboot with what ever device you want to then.
:lolflag:

Hi!

Hey this might be a dump question hehe

I supose it is possible to do the same, but running windows 7 on the internal drive; and ubuntu from the external one.

Is it possible?

---

### Post by Mark Phelps on 2011-09-04
> **krlosjcc said:**
> ... I supose it is possible to do the same, but running windows 7 on the internal drive; and ubuntu from the external one.

Is it possible?

Not only is it possible, it's probably the ONLY way this is going to work.  MS does NOT generally support running their OS's (especially recent ones) from an external drive.

Notice that days have gone by and we haven't heard back regarding whether the other approach worked.  My guess, from my own experience, is that it did NOT and the OP didn't feel like returning to admit that.

---

