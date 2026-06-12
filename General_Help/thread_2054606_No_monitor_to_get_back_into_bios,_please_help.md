---
title: "No monitor to get back into bios, please help"
date: 2012-09-07
forum: General Help
---

### Post by Lost with Linux on 2012-09-07
OK so I know this was a foolish mistake but can you help me anyway? 

After updating to Ubuntu 11.10, I was looking through the bios because my nic would not recognize my network cable. Sweet, found it was disabled in the bios. Unfortunately while I was there I saw an option to change my monitor from CRT to LCD. Sounded great! I have an LCD monitor so I changed it. Well now I have a black screen so I  can't find my way to get back into the bios to change it back...

What's a fool to do. This has been quite the learning experience.

Thanks

---

### Post by cryptotheslow on 2012-09-07
Unless you have or can get hold of another screen that does work with it in its current configuration then I think your only option is to reset the BIOS settings. Typically this is done by moving (or removing) a jumper on the motherboard itself.

What make and model is the motherboard?

---

### Post by Lost with Linux on 2012-09-07
Via Apia M1000 is what it says on the box. The motherboard has a video output that I put into the TV and I can see part of the screen but it doesn't come up until it is fully booted so I can't see any of the bios screens. The S video jack appears to be disabled.

---

### Post by cryptotheslow on 2012-09-07
Do you mean **E**pia rather than Apia?

If so the manual can be found here:
[http://de.viatech.com/de/products/embedded/LegacyProducts.jsp?productLine=1&id=81&tabs=1](http://de.viatech.com/de/products/embedded/LegacyProducts.jsp?productLine=1&id=81&tabs=1)

Have a look at page 33. You need to power off and move the CLEAR_CMOS jumper (next to the battery) to pins 2 and 3 for a short time. Then move it back to pins 1 and 2 **_before_** powering back on.

If it is actually **A**pia post back and I'll see if I can find the relevant instructions.

---

### Post by Lost with Linux on 2012-09-07
Perfect!!!! worked like a charm.

Thanks for your help

---

### Post by cryptotheslow on 2012-09-07
Glad it worked out :D You may want to take a quick look through your BIOS settings to check for any settings that need putting back after the reset.

Use the Thread Tools option near your opening post to mark the thread as solved :D

---

