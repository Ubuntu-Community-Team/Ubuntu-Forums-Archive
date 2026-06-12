---
title: "&quot;Legacy&quot; ATI drivers for Radeon X1300"
date: 2011-06-16
forum: General Help
---

### Post by brad1138 on 2011-06-16
I have a PCIE X1300 256 MB laying around and bench marked it with Passmark in XP (my comp is dual boot). I found it to be a lot faster than the HD3000 integrated video of the motherboard of the new comp I just built (MSI 760GM w/Phenom II 955). I will be getting a new Video card later, probably an ATI 4890 or Nvidia GTX 275 or so.

When I booted into Ubuntu, it doesn't list a proprietary driver for it like it did for the HD3000. 

I found [this]("http://www2.ati.com/drivers/linux/linux_8.24.8.html") page which I think has the proper driver for it. But is this an old driver from the days when ATI/Linux drivers were horrible?

Should I try this driver or am I better off just using the on-board video until I get a new video card?

Thanks,
Brad

---

### Post by brad1138 on 2011-06-16
OK, forget above. I found the proper driver [here]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English"). It says "32-Bit packages must be installed for 64-Bit Linux drivers to install or work." at the bottom of the page. 

Is it a good idea to do that, and how do I do that?

---

### Post by coldraven on 2011-06-16
From the link "Automated installer and Display Drivers for X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, or 7.4"
I think Natty uses XOrg 7.5 or higher so it would not work. That is why it does not show up in "proprietary drivers".
I'm stuffed, my laptop has the X1250 card :( But it runs well, just not for games.

---

### Post by brad1138 on 2011-06-16
> **coldraven said:**
> From the link "Automated installer and Display Drivers for X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, or 7.4"
I think Natty uses XOrg 7.5 or higher so it would not work. That is why it does not show up in "proprietary drivers".
I'm stuffed, my laptop has the X1250 card :( But it runs well, just not for games.

Thanks, I think I will just go back to the onboard video, not worth the hassle.

---

