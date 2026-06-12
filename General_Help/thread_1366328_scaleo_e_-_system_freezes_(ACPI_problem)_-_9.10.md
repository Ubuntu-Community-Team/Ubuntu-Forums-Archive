---
title: "scaleo e - system freezes (ACPI problem) - 9.10"
date: 2009-12-28
forum: General Help
---

### Post by lipos on 2009-12-28
I decided to install myslef Ubuntu 9.10 and create a media center, but my system was freezing during installation. 
After adding acpi=off I was able to install it without any problems.

I'm running it on Fujitsu-Siemens Scaleo E hardware with 2 x P4 3.4 GHz, 2,5 GB RAM and Intel 82915G integrated graphics.

After installation when running without acpi=off everything runs well. Two CPUs are being used and graphics is not creating problems. The problem is that it's crushing after 2mins of bootup.
On the other hand, when running acpi=off it's not crushing at all, but only one CPU is being discovered and the whole machine is being extremely slow - xorg is taking 70% - 90%.
I tried a number of boot options but I was never able to have both - two cpus/fast graphics and stable machine.

I tried:
> acpi=off
acpi=force
acpi=force pci=noacpi
noapic
nolapic


After 

> acpi=ht

 two CPUs are being discovered but grapgics is still slow :/

It sees that ACPI is my problem.
What are my oprions? APM would help me?

---

### Post by lipos on 2010-01-03
Here's my fix:

I left acpi=ht in grub and reverted to 8.10 intel drivers using:

[http://www.webupd8.org/2009/05/reverting-xorg-video-intel-driver-of.html]("http://www.webupd8.org/2009/05/reverting-xorg-video-intel-driver-of.html")

I see two CPUs, and graphics runs well.

Hope this will help someone since I lost a lot of time on it :)

---

