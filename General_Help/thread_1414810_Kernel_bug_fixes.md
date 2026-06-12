---
title: "Kernel bug fixes"
date: 2010-02-24
forum: General Help
---

### Post by IceCap on 2010-02-24
I'm running Mythbuntu 9.10 (xubuntu) on my mediacenter and due to kernel bugs I'm forced to switch between two versions in order to juggle things to work:

[LIST]
[*]2.6.31-19: latest Karmic kernel.  Wireless doesn't work due to some bug in the kernel such that ndiswrapper doesn't work properly (known bug, multiple references to this bug on the forum).  This is what I have the system boot to most of the time.
[*]2.6.32-10: Mainline Lucid kernel.  Wireless works fine here (every single time) but ACPI doesn't work (also known bug).  My remote doesn't work on this kernel either but I'm assuming that is because this is a mainline kernel.  I boot to this one to get my listings data.
[/LIST]

  I'm trying to figure out if there are other kernels out there where both wireless AND ACPI will work (would that be too much to ask for?) but I'm having a hard time deciphering the various bug fixes in each version.  I'm also not sure where these two bugs rank in terms of urgency (one would think wireless is important).

  Does anyone have any idea which kernel I should try or where I can find some more easily digestible information about the kernel versions?

  BTW, my wireless card uses a RTL 8190 chip and thus needs ndiswrapper.

  Thanks

  IC

---

### Post by cariboo on 2010-02-24
Sometimes it's more cost effective to replace the non-supported hardware with something that is supported. I've seen supported usb wireless devices for $20.00. For me it is better to replace the device if it isn't supported, than to spend days trying to get it to work.

---

### Post by IceCap on 2010-02-24
> **cariboo907 said:**
> Sometimes it's more cost effective to replace the non-supported hardware with something that is supported. I've seen supported usb wireless devices for $20.00. For me it is better to replace the device if it isn't supported, than to spend days trying to get it to work.

  Given that it is a bug that I'm dealing with, how can I be sure that the next bug doesn't break support of the supported hardware?  We are talking about a known bug, with a solution already out there (the 2.6.32 kernel) but no back port.  Ndiswrapper may be a hack, but it appears to be working for a large number of different wireless (and wired I guess) hardware and as such, a very effective solution for supporting hardware.

  But, you point is well taken, I could make my life easier by finding a wireless adapter that doesn't require ndiswrapper.

  Thanks

  IC

---

