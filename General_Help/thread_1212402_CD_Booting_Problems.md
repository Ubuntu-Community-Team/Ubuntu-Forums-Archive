---
title: "CD Booting Problems"
date: 2009-07-13
forum: General Help
---

### Post by BigEngland on 2009-07-13
Hi all,

I've found that ever since I installed Ubuntu Jaunty 9.04 I haven't been able to boot anything from a disk during boot up. I have tried adjusting the boot options to CD first etc and all the other technical things in BIOS and none of that worked.

I'm looking for a way to run my Windows installation CD and to install it onto my other hard drive (Love Ubuntu but need some Win-only programs). Not as a dual boot option but just to install it as two separate operating systems.

I believe that the GRUB loader is messing up the CD's when they try to load as they run on the other pc's in the house.

My problem - I want to boot from a CD during start-up but I think that the GRUB is stopping this

Please help!
Many thanks to all that offer help,
BigEngland

---

### Post by BigEngland on 2009-07-13
I'm afraid i'm bumping this cause I really could do with some help :(

---

### Post by merlinus on 2009-07-13
I would seriously doubt that grub is causing your problem, since it resides on your hdd and you are trying to boot from the cd drive first.

So you might check the cd drive connectors, etc., try other bootable cds, and press whatever  F key that on startup offers booting options for your computer.

---

### Post by BigEngland on 2009-07-13
Nope, none of them work. I tried - Knoppix Live DVD, Ubuntu 9.04 boot cd, Windows 7 Candidate Release DVD and my 2 Windows XP disks.

No problems before installing Ubuntu so that's why I think it's causing the problem. Can anyone give me help in manually installing Windows without having to boot via CD?

---

### Post by merlinus on 2009-07-13
Sounds like a cd drive gone bad.  Can you borrow an external one?

---

### Post by lisati on 2009-07-13
> **merlinus said:**
> Sounds like a cd drive gone bad.  Can you borrow an external one?

Another possibility is the BIOS settings have been messed up and the CD drive isn't being recognized properly. Most of the machines I've used have some kind of "restore to default settings" option. When I've used this on my old Win98 machine I have to then had to get the BIOS to autodetect the disk & CD drives in my machine, but my newer machines usually get it correct.

---

### Post by BigEngland on 2009-07-13
> **merlinus said:**
> Sounds like a cd drive gone bad.  Can you borrow an external one?

I have one but i don't have a power adaptor, that is unless you could help me find a 9v ac adaptor with a laptop-style end

---

### Post by BigEngland on 2009-07-13
> **lisati said:**
> Another possibility is the BIOS settings have been messed up and the CD drive isn't being recognized properly. Most of the machines I've used have some kind of "restore to default settings" option. When I've used this on my old Win98 machine I have to then had to get the BIOS to autodetect the disk & CD drives in my machine, but my newer machines usually get it correct.

Ah yes, I also tried that with the other settings in BIOS when i had finished trying all the adjustments. The current settings are on default and the CD drive is recognised but doesn't boot. Nothing is wrong with the cd's as 3 out of 5 of the cd's are original (all the windows)

---

