---
title: "ubuntu 10.10 64bit does funky things"
date: 2011-02-27
forum: General Help
---

### Post by daveboy23 on 2011-02-27
ok, this is totally weird and i have no idea what's happening.
i have a 64bit ubuntu 10.10 (just like the title says).  i've been having random (really out of the blue) slow ubuntu response.  so slow, the mouse pointer works stops works kinda thing.  i can't open any program and clicking the power button doesn't work.  i have to hard restart it (holding down the power for a couple of sec).  this is really making me mad since i'm afraid for my hardware life and to be honest - not very impressed with ubuntu.

i have no idea why this happens and i really need help on this subject, otherwise i'd just have to look for another OS (and i would like not to)
also - the computer is new so i don't think it's a hardware problem, but if there are tests i can do to check it i wouldn't mind

thanks everybody

---

### Post by 3rdalbum on 2011-02-27
> **daveboy23 said:**
> ok, this is totally weird and i have no idea what's happening.
i have a 64bit ubuntu 10.10 (just like the title says).  i've been having random (really out of the blue) slow ubuntu response.  so slow, the mouse pointer works stops works kinda thing.  i can't open any program and clicking the power button doesn't work.  i have to hard restart it (holding down the power for a couple of sec).  this is really making me mad since i'm afraid for my hardware life and to be honest - not very impressed with ubuntu.

i have no idea why this happens and i really need help on this subject, otherwise i'd just have to look for another OS (and i would like not to)
also - the computer is new so i don't think it's a hardware problem, but if there are tests i can do to check it i wouldn't mind

thanks everybody

"Everything becoming slow" and "turning the computer off at the power point" will not damage your hardware.

However, it does sound like your hardware is damaged. I had the same symptoms and it turned out to be caused by bad RAM.

Linux uses as much RAM as it can; waste not, want not. Windows tends to allocate up to 2 GiB to the Windows kernel which really doesn't need that much, so basically a lot of your RAM goes unused. If there's a bad part of your RAM module that lies at the upper end of the Windows kernel's 2 GiB space, then you might never have a problem on Windows.

I'd recommend a thorough memory test; try Memtest86+ at the GRUB menu, or a physical "take a RAM module out and see if the crashes stop" test.

---

### Post by daveboy23 on 2011-02-27
OK, you'll have to be a little more clear about the Memtest86+ at the grub.  seeing as i am a noob i'd need more info as in - how to do it?

in anycase, it doesn't seem to me like it could be a hardware problem (seeing as this is a new computer) but i'll try it anyway just to make sure.

thanks

---

