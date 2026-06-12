---
title: "Non-Executable Memory"
date: 2010-05-07
forum: General Help
---

### Post by autonomy on 2010-05-07
Hello, I don't see anything like [this]("https://wiki.ubuntu.com/Security/CPUFeatures") in my BIOS. ("Execute Disable Bit") The flags line contains pae, and the CPU has NX capabilities. American Megatrends doesn't support the BIOS, and my computer manufacture isn't helping me either.

---

### Post by sylvester_0 on 2010-05-07
My parent's old-ish Dell has the same issue. I hope I'm not giving bad security advice here, but I wouldn't worry about it.

---

### Post by rory526 on 2010-08-16
I also have the same problem. My BIOS manufacturer is Insyde. I suspect NX capabilities were removed in a BIOS update installed recently as I now receive warnings upon logging into a virtual terminal that I don't remember being there before.

As with you, there is no option in my BIOS to turn NX on. I have seen a similar issue with an Insyde BIOS here:

[http://h30434.www3.hp.com/t5/Hardware/Insyde-BIOS-Silently-Disables-NX-DX-DEP-Security-Features/m-p/291826](http://h30434.www3.hp.com/t5/Hardware/Insyde-BIOS-Silently-Disables-NX-DX-DEP-Security-Features/m-p/291826)

---

### Post by dankdave on 2010-12-31
Same issue.

The computer I have is 

Dell System GX280
BIOS Version: A04 (02/09/05)
Intel(R) Pentium(R) 4 CPU 3.4GHz
1.0 GB 533 MHz DDR2 SDRAM

Anyone know if this should be a concern or if there's anything that can be done about it?

---

