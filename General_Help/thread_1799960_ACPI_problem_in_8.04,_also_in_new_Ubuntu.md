---
title: "ACPI problem in 8.04, also in new Ubuntu?"
date: 2011-07-08
forum: General Help
---

### Post by Iceberg76 on 2011-07-08
I am running Ubuntu 8.04 (it's discontinued, I know) in an ASUS laptop. I'd had to turn ACPI off, otherwise, it would not start. I could update the BIOS, to correct this problem, but on this laptop that's not doable.

Without ACPI, sound is turned off too (which is a pity).

If I update to the latest Ubuntu, will this problem persist?

---

### Post by dino99 on 2011-07-08
the big difference with new distro is the kernel, which have much more features & fixes than previous. So if your software is able to run ubuntu natty, install it, otherwise select Lubuntu. And read xsession-errors & kern.log to know about errors (that can help to resolve issue :))

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by Iceberg76 on 2011-07-08
Thanks for the prompt answer.

The update manager offers me the 10.04 LTS. Would that be much different from the present 8.04 that I have right now?

---

### Post by OldBoy44 on 2011-07-08
10.04 is very stable and a good choice! - :)

I have never used 8.04 so can't compare.

---

### Post by Iceberg76 on 2011-07-08
Yes, 8.04 is also a good choice. The problem is that its ACPI features are not compatible with my mainboard. The funny thing is that Puppy Linux, a much more primitive Linux distribution, don't pose such problems to run in my laptop. So, if 10.04 is not much different, then I won't even try...

---

### Post by dino99 on 2011-07-08
often solutions are found by users having the same issue, i mean the same chipset than yours, so googling around ubuntu+yourchipset might give you some ideas :)

to find it (in case you dont know about it)

into a terminal:

lspci -vvvnn > chipset.txt

---

