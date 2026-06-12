---
title: "Kernel hangs on Asus M6N when ACPI is enabled"
date: 2006-02-01
forum: General Help
---

### Post by chopmo on 2006-02-01
One of the very few problems I have with Ubuntu Breezer is that the system simply locks up from time to time. I have not been able to see a pattern in this behaviour, sometimes it hangs after 10 minutes, sometimes I can work half a day without problems (typically somewhere in between, though). 

I get absolutely no warning, it just stops responding to mouse, keyboard, ping, ssh....completely frozen. No HDD activity, no LED activity, screen frozen. 

Out of bitter experience with the ASUS, I tried passing the "acpi=off" kernel option in GRUB, and it is stable again (but I sure do miss ACPI :( ). I am also passing "noapic" and "nolapic" in GRUB (required for proper shutdown). 

/var/log/messages shows nothing of interest after a crash. Are there other logfiles I should check?

I suspect this is a hardware problem, but I don't really know how to narrow it down. I have tried using both the "ati" and the "fglrx" X drivers (graphics card is a Mobility Radeon 9600). 

Any suggestions? 

Thanks in advance,
Jacob

---

